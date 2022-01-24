<template>
  <div id="app">

    <Time/>
    <Search/>
    <QuickLink/>
    <Setting/>
  </div>
</template>

<script>
import Time from './components/Time.vue'
import Search from './components/Search.vue'
import QuickLink from './components/QuickLink.vue'
import Setting from './components/Setting.vue'

export default {
  name: 'App',
  components: {
    Time,Search,QuickLink,Setting
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
