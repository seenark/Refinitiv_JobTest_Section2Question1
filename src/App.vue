<template>
  <div id="app">
    <Cal></Cal>
  </div>
</template>

<script>
import Cal from "./components/Cal";

export default {
  name: "App",
  components: {
    Cal,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
