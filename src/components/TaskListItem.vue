<template>
  <div>
    <input type="checkbox" :checked="task.isDone" @change="onToggleTask" />
    <span>{{task.name}}</span>
    <button type="button" @click="onDeleteTask">Remove</button>
  </div>
</template>

<script>
export default {
  name: "TaskListItem",
  props: ["task"],
  methods: {
    onDeleteTask() {
      this.$emit("deleteTask", this.task);
    },
    onToggleTask() {
      this.$emit("toggleTask", this.task);
    }
  }
};
</script>

<style scoped>
</style>