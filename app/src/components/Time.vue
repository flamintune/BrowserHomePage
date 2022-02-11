<template>
  <div>
    <!-- {{ now }} -->
    <span class="animated infinite bounce">
      {{ hour }} : {{ minute }} : {{ second }}
    </span>
  </div>
</template>

<script>
import moment from "moment";
import "animate.css";
// 用于显示时间的一个组件
export default {
  name: "Time",
  data() {
    return {
      now: moment().format("HH:mm:ss"),
      hour: moment().format("HH"),
      minute: moment().format("mm"),
      second: moment().format("ss"),
    };
  },
  mounted() {
    setInterval(() => {
      this.hour = moment().format("HH");
      this.minute = moment().format("mm");
      this.second = moment().format("ss");
    }, 1000);
  },
  methods: {
    countTime() {
      // console.log('???')
    },
  },
  computed: {},
  watch: {},
};
</script>

<style scoped>
span {
  font-family: fantasy;
  font-size: 92px;
  color: white;
  font-weight: inherit;
  animation: bounce;
  animation-duration: 2s;
  transition: all 0.5s ease-in-out;

}
span:hover {
  font-size:100px;
  transition: all 0.5s ease-in-out;
}
/* span: */
</style>