<template>
  <h2>Welcome to my calendar</h2>
  <CalendarCom />
</template>

<script>
import CalendarCom from "./components/Calendar.vue";
export default {
  name: "App",
  components: { CalendarCom },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: rgb(245, 244, 244);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  /* margin-top: 60px; */
}
</style>
