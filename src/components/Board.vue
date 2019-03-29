<template>
  <div class="board">
    <category :key="i" v-for="(category, i) in board.categories" :category="category"></category>
  </div>
</template>

<script>
import Category from "./Category";

export default {
  name: "Board",
  props: ["board"],
  components: {
    Category
  }
};
</script>