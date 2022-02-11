<template>
  <div id="app" ref="app" :style="{ backgroundImage: color }">
    <Time />
    <Search />
    <QuickLink />
    <Setting @click.native="ShowSettingDialog" />
    <setting-dialog
      v-if="showSetting"
      @backgroundColorToggle="BackgroundToggole"
      @closeDialog="close"
    />
  </div>
</template>

<script>
import Time from "./components/Time.vue";
import Search from "./components/Search.vue";
import QuickLink from "./components/QuickLink.vue";
import Setting from "./components/Setting.vue";
import settingDialog from "./components/settingDialog.vue";

export default {
  name: "App",
  components: {
    Time,
    Search,
    QuickLink,
    settingDialog,
    Setting,
  },
  data() {
    return {
      showSetting: false,
      color: "",
    };
  },
  methods: {
    BackgroundToggole(e) {
      // background-image: linear-gradient(180deg, #21d4fd 0%, #b721ff 100%);
      console.log(this.$refs.app.style);
      // this.$refs.app.style.backgroundColor = e.color1;
      this.color = `linear-gradient(180deg,${e.color1} 0%, ${e.color2} 100%)`;
      console.log(this.$refs.app.style);
      let rgb = this.colorRgb(e.color1);
      const graylevel = rgb[0] * 0.299 + rgb[1] * 0.587 + rgb[2] * 0.114;
      if (graylevel >= 192) this.$refs.app.style.color = "#000";
      else this.$refs.app.style.color = "#FFF";
    },
    close() {
      this.showSetting = false;
    },
    ShowSettingDialog() {
      this.showSetting = true;
    },
    colorRgb(e) {
      let color = e.toLowerCase();
      if (color.length === 4) {
        let colorNew = "#";
        for (let i = 1; i < 4; i += 1) {
          colorNew += color.slice(i, i + 1).concat(color.slice(i, i + 1));
        }
        color = colorNew;
      }
      // 处理六位的颜色值，转为RGB
      let colorChange = [];
      for (let i = 1; i < 7; i += 2) {
        colorChange.push(parseInt("0x" + color.slice(i, i + 2)));
      }
      return colorChange;
    },
  },
  mounted() {
    this.$refs.app.style.backgroundColor = this.appColor;
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 90px;
  padding-bottom: 120px;
  width: 100%;
  height: 100%;
  /* background-color:#21d4fd; */
  /* background-image: linear-gradient(180deg, #21d4fd 0%, #b721ff 100%); */
  background-color: #ffffff;
  background-image: linear-gradient(
    180deg,
    #ffffff 0%,
    #6284ff 50%,
    #ff0000 100%
  );
}
</style>

