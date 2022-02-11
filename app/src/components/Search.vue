<template>
  <div id="wrapper">
    <div id="search">
      <form :action="`https://${searchOptions}`" method="get" ref="form">
        <!-- <input type="hidden" name="cl" value="3" /> -->
        <input
          type="search"
          placeholder="搜索"
          v-model="searchValue"
          :name="searchParam"
          ref="search"
        />
        <div id="icon" @click="submit"></div>
      </form>
    </div>
    <!-- <form action="http://www.baidu.com.cn/s" method="get"> -->
    <!-- <input type="submit" value="百度一下" /> -->
    <!-- </form> -->
  </div>
</template>

<script>
// 用于显示搜索栏的一个组件
export default {
  name: "Search",
  data() {
    return {
      searchValue: "",
      searchOptions: "baidu.com/s",
      searchParam: "wd",
    };
  },
  mounted() {
    this.$refs.search.focus();
  },
  methods: {
    searchToggle() {},
    submit() {
      this.$refs.form.submit();
    },
  },
};
</script>  
<style scoped>
#search {
  display: flex;
  position: relative;
  align-content: center;
  justify-content: center;
}

input {
  width: 750px;
  border-radius: 15px;
  padding: 10px;
  border: none;
  outline: none;
  background: rgb(255, 255, 255);
  box-shadow: 50%;
}
/* input[type="search"] {
  -webkit-appearance: none;
} */
input::-webkit-search-cancel-button {
  display: none;
}
#icon {
  width: 30px;
  height: 30px;
  background-image: url("../assets/search.png");
  background-repeat: space;
  position: relative;
  top: -1.7em;
  right: -35.6em;
  /* background-color: rgb(206, 105, 105); */
  background-size: 100%;
  transition: all 0.5s linear;

}
#icon:hover {
  background-size: 110%;
  transition: all 0.3s ease-in-out;
}
#wrapper {
  margin-top: 50px;
  margin-bottom: 30px;
}
</style>