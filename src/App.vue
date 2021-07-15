<template>
  <List />
</template>

<script>
import List from "./components/List.vue";

export default {
  name: "App",
  components: {
    List,
  },
};
</script>

<style>
body {
  margin: 0px;
}
#app {
  display: flex;
  flex-flow: column;
  align-items: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #c5c3c3;
  height: 100vh;
}
</style>
