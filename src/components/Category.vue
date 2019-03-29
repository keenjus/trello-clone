<template>
  <section class="category">
    <header class="category__header">
      <div class="category__header__title">{{ category.title }}</div>
    </header>
    <main class="category__body">
      <draggable :list="category.tasks" group="categories" draggable=".task">
        <task :key="i" v-for="(task, i) in category.tasks" :task="task" @delete="deleteTask"></task>
      </draggable>
    </main>
    <footer class="category__footer">
      <button class="button is-small" @click="showCreateTaskModal()">Add task</button>
    </footer>
    <modal name="create-task-modal" height="auto">
      <create-task @create="createTask" @close="hideCreateTaskModal()"></create-task>
    </modal>
  </section>
</template>

<script>
import Draggable from "vuedraggable";
import Modal from "vue-js-modal";
import Task from "./Task";
import CreateTask from "./CreateTask";

export default {
  name: "Category",
  props: ["category"],
  components: {
    Draggable,
    Modal,
    Task,
    CreateTask
  },
  data() {
    return { createdTask: {} };
  },
  methods: {
    deleteTask(task) {
      const index = this.category.tasks.indexOf(task);
      if (index === -1) return;

      this.category.tasks.splice(index, 1);
    },
    createTask(newTask) {
      this.category.tasks.push(newTask);
    },
    showCreateTaskModal() {
      this.$modal.show("create-task-modal");
    },
    hideCreateTaskModal() {
      this.$modal.hide("create-task-modal");
    }
  }
};
</script>

<style lang="scss" scoped>
form {
  padding: 20px;
}
</style>
