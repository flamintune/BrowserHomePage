<template>
  <div id="wrapper">
    <div id="quicklink">
      <div v-for="(item, index) in links" :key="index">
        <template v-if="index < 10">
          <div class="link" v-if="item.img != '../assets/add.png'">
            <div class="more" @click="editLinks(index)">
              <img src="../assets/more.png" alt="" />
            </div>
            <div class="item">
              <a :href="item.img">
                <img
                  :src="`${item.img}/favicon.ico`"
                  onerror="onerror=null;this.src='/img/error.17918046.png'"
                  alt=""
                />
              </a>
            </div>
            <p>
              {{ item.title }}
            </p>
          </div>
          <div class="link" v-else>
            <div class="add"></div>
            <div class="item" @click="addDialog(index)">
              <img src="../assets/add.png" alt="" />
            </div>
            <p>
              {{ item.title }}
            </p>
          </div>
        </template>
      </div>
    </div>
    <Dialog
      v-if="showDialog"
      @closeDialog="close"
      @submitDialog="submit"
      @deleteLink="deleteLink"
      @addLink="addLink"
      v-bind:link="link"
    ></Dialog>
  </div>
</template>

<script>
// 用于显示快捷方式的图标的
import Dialog from "./linkDialog.vue";
export default {
  name: "QuickLink",
  data() {
    return {
      links: [
        { img: "https://www.bing.com", title: "bing" },
        { img: "https://www.baidu.com", title: "baidu" },
        { img: "https://www.github.com", title: "github" },
        { img: "https://www.bilibili.com", title: "bilibili" },
        { img: "https://react.docschina.org", title: "react" },
        { img: "https://juejin.cn", title: "掘金" },
        { img: "https://interactjs.io", title: "interactjs" },
        { img: "../assets/add.png", title: "添加" },
      ],
      imgUrl: [],
      showDialog: false,
      link: {
        index: "",
        name: "",
        Url: "",
      },
    };
  },
  components: { Dialog },
  methods: {
    editLinks(e) {
      console.log(e);
      this.showDialog = true;
      this.link = this.links[e];
      this.link.index = e;
      // 点击时将 e 传入
      // console.log(this)
    },
    errorImg() {
      return "this.οnerrοr=null;this.src=" + '"' + "../assets/error.png" + '";';
    },
    close() {
      this.showDialog = false;
    },
    submit(e) {
      this.showDialog = false;
      this.links[e.index].title = e.name;
      this.links[e.index].img = e.Url;
      console.log(e);
    },
    deleteLink(e) {
      this.showDialog = false;
      this.links = this.links.filter((element, index) => index != e);
    },
    addDialog(e) {
      console.log(e);
      this.showDialog = true;
      this.link = { add: true };
      this.link.index = e;
    },
    addLink(e) {
      this.showDialog = false;
      let temp = {
        img: this.links[e.index].img,
        title: this.links[e.index].title,
      };
      this.links[e.index].title = e.name;
      this.links[e.index].img = e.Url;
      this.links.push(temp);
    },
  },
};
</script>

<style scoped>
#wrapper {
  /* width:1000px; */
  text-align: center;
  padding-bottom: 166px;
}
#quicklink {
  max-width: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  overflow: hidden;
  justify-content: space-around;
  padding-left: 400px;
  padding-right: 400px;
  white-space: nowrap;
}
.link {
  width: 100px;
  height: 100px;
  padding: 20px;
  padding-top: 0;
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-content: center;
  align-items: center;
  font-size: 20px;
}
.item {
  width: 50px;
  height: 50px;
  background-color: rgb(255 255 255 / 20%);

  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  /* background-color: white; */
}
p {
  margin: 0;
  /* color:white; */
}
.item img {
  width: 25px;
  height: 25px;
}

.link:hover {
  background-color: rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  backdrop-filter: blur(100px);
}
.more {
  width: 25px;
  height: 25px;
  opacity: 0;
  background-color: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  position: relative;
  top: 10px;
  left: 45px;
  /* opacity: 1; */
  margin: 0;
  padding: 0;
}
.more img {
  width: 25px;
  height: 25px;
}
.more:hover {
  opacity: 1;
}
.add {
  width: 25px;
  height: 25px;
  margin: 0;
  padding: 0;
}
</style>