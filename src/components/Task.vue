<template>
  <div class="task" :class="{'is-archived': task.archived}">
    <div class="task__body">{{ task.title }}</div>
    <div class="task__footer">
      <button class="button is-danger is-small" @click="$emit('delete', task)">DELETE</button>
      <button
        class="button is-warning is-small"
        @click="task.archived = !task.archived"
      >{{ task.archived ? 'UNARCHIVE' : 'ARCHIVE' }}</button>
      <button class="button is-primary is-small">OPEN</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"]
};
</script>