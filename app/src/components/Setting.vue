<template>
  <div>
    <div id="bgsetting">
    <div id="setting"></div>
    </div>
  </div>
</template>

<script>
import settingDialog from "./settingDialog.vue";
export default {
  name: "Setting",
  data() {
    return {};
  },
  methods: {
  },
  component: settingDialog,
};
</script>

<style scoped>
#setting {
  background-size: 100%;
  background-image: url("../assets/setting.png");
  position: fixed;
  width: 40px;
  height: 40px;
  top: 20px;
  right: 20px;
}
#setting:hover {
  /* size:120%;
  background:rgb(255 255 255 / 20%); */
  border:1px solid rgba(255, 255, 255, 0.219);
  background-color:rgba(0, 0, 0, 0.116);
  border-radius: 50%;
}
</style>