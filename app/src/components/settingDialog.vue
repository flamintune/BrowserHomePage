<template>
  <div id="dialog">
    <div class="border">
      <div @click="closeDialog" class="closeImg"></div>
      <div id="color">
        <p>选择背景颜色</p>
        <!-- <colorPicker v-model="color" v-on:change="handleChangeColor" :default-color="color"></colorPicker> -->
      </div>
      <div class="colorWrapper">
        <div v-for="(item, index) in colors" :key="index">
          <template>
            <div class="colorPick" @click="backgroundColorToggle(index)">
              <div class="color1" :style="{backgroundColor:colors[index].color1}"></div>
              <div class="color2" :style="{backgroundColor:colors[index].color2}"></div>
            </div>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  name: "settingDialog",
  data() {
    return {
      color: "#ffffff",
      colors: [
        { color1: "#faaca8", color2: "#ddd6f3" },
        { color1: "#08aeea", color2: "#2af598" },
        { color1: "#21d4fd", color2: "#b721ff" },
        { color1: "#8ec5fc", color2: "#e0c3fc" },
        { color1: "#97D9E1", color2: "#D9AFD9" },
        { color1: "#fbda61", color2: "#ff5acd" },
        { color1: "#A9C9FF", color2: "#FFBBEC" },
        { color1: "#8BC6EC", color2: "#9599E2" },
        { color1: "#FFDEE9", color2: "#B5FFFC" },
        { color1: "#f43f8b", color2: "#b652dd" },
      ],
    };
  },
  props: ["appColor"],
  methods: {
    handleChangeColor() {
      this.$emit("handleChangeColor", this.color);
    },
    closeDialog() {
      this.$emit("closeDialog");
    },
    backgroundColorToggle(e)
    {
      this.$emit("backgroundColorToggle",this.colors[e])
    }
  },
  mounted() {
    this.color = this.appColor;
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
  width: 45%;
  height: 59%;
  position: absolute;
  left: 50%;
  top: 55%;
  transform: translate(-50%, -50%);
  overflow: hidden;
}

#color {
  margin-top: 5%;
  display: flex;
  justify-content: center;
  align-items: center;
}

#color p {
  margin-right: 10px;
}

.colorPick {
  display: flex;
  justify-content: center;

  padding:20px;
}
.color1 {
  width: 32px;
  height: 64px;
  border-radius: 50%;
  background-color: white;
  border-radius:32px 0 0 32px;
}
.color2 {
  width: 32px;
  height: 64px;
  border-radius:0 32px 32px 0;
  background-color: black;
}
.colorWrapper {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 100%;
  margin:30px 50px;
  overflow: hidden;
}
</style>