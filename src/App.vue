<template>
  <div id="app">
    <board :board="board"></board>
  </div>
</template>

<script>
import Board from "./components/Board";
import "./styles/main.scss";

export default {
  name: "App",
  components: {
    Board
  },
  data() {
    return {
      board: {
        categories: [
          {
            title: "TODO",
            tasks: []
          },
          {
            title: "TODO2",
            tasks: []
          }
        ]
      }
    };
  },
  mounted() {}
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
