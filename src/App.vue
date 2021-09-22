<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Counter />
    <Timer />
    <StudentList />
  </div>
</template>

<script>
import Counter from "./components/Counter.vue";
import Timer from "./components/Timer.vue";
import StudentList from "./components/StudentList.vue"

export default {
  name: "App",
  components: {
    Counter,
    Timer,
    StudentList
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
  margin-top: 60px;
}
</style>
