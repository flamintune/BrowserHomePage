<template>
  <div id="dialog">
    <div class="border">
      <div @click="closeDialog" class="closeImg"></div>
      <p>编辑快捷链接</p>
      <div class="editinput">
        <p class="editname">名称</p>
        <input type="text" v-model="linkprops.name" />
      </div>
      <div class="editinput">
        <p class="editname">网址</p>
        <input type="text" v-model="linkprops.Url" />
      </div>
      <div class="btn">
        <button class="cancel" @click="deleteLink" v-if="!linkprops.add">
          删除
        </button>
        <button class="success" @click="submitDialog" v-if="!linkprops.add">
          完成
        </button>
        <button class="success" @click="addLink" v-else>完成</button>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  name: "Dialog",
  data() {
    return {
      linkprops: {
        index: this.link.index,
        name: this.link.title,
        Url: this.link.img,
        add: this.link.add,
      },
    };
  },
  props: {
    link: Object,
  },
  methods: {
    closeDialog() {
      //给父组件传参
      this.$emit("closeDialog", false);
    },
    submitDialog() {
      this.$emit("submitDialog", this.linkprops);
    },
    deleteLink() {
      this.$emit("deleteLink", this.link.index);
    },
    addLink() {
      this.$emit("addLink", this.linkprops);
    },
  },
};
</script>
 
<style scoped>
#dialog {
  position: fixed;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.3);
  width: 100%;
  height: 100%;
  color: white;
}
.closeImg {
  width: 30px;
  height: 30px;
  float: right;
  margin-right: 5px;
  margin-top: 5px;
  cursor: pointer;
  background-image: url(../assets/close.png);
  background-size: cover;
  background-repeat: no-repeat;
}
.border {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.719);
  border-radius: 20px;
  width: 40%;
  height: 50%;
  position: absolute;
  left: 50%;
  top: 55%;
  transform: translate(-50%, -50%);
}
input {
  text-decoration: none;
  border-radius: 12px;
  padding: 8px;
  padding-left: 10px;
  width: 80%;
  border: none;
  outline: none;
}
p {
  text-align: center;
}
.editname {
  position: relative;
  left: -42%;
  margin: 0;
  padding: 0;
  margin: 10px 0;
}
.btn {
  margin-top: 100px;
  display: flex;
  justify-content: space-around;
}
button {
  width: 20%;
  border-radius: 10px;
  border: none;
  padding: 5px;
  background-color: white;
  outline: none;
}
.cancel {
  color: red;
}
.success{
  color:green;
}
</style>