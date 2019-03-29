<template>
  <form v-on:submit.prevent="submit()">
    <div class="field">
      <label class="label">Title</label>
      <div class="control">
        <input v-model="newTask.title" class="input" type="text" placeholder="Title of the task">
      </div>
    </div>
    <div class="field is-grouped">
      <div class="control">
        <button type="submit" class="button is-link">Submit</button>
      </div>
      <div class="control">
        <button type="button" class="button is-text" @click="$emit('close')">Cancel</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "CreateTask",
  props: [],
  data() {
    return { newTask: {} };
  },
  methods: {
    submit() {
      const newTask = Object.assign({}, this.newTask);
      this.$emit("create", newTask);
      this.$emit("close");
      this.newTask = {};
    }
  }
};
</script>