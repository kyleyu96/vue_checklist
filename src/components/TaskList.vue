<template>
  <div>
    <TaskListItem
      v-for="(task, index) in toShow"
      :task="task"
      :key="index"
      @deleteTask="onDeleteTask"
      @toggleTask="onToggleTask"
    />
  </div>
</template>

<script>
import TaskListItem from "./TaskListItem";

export default {
  name: "TaskList",
  components: {
    TaskListItem
  },
  props: ["tasks", "filter"],
  computed: {
    toShow() {
      switch (this.filter) {
        case "all":
          return this.tasks;
        case "active":
          return this.tasks.filter(task => !task.isDone);
        case "done":
          return this.tasks.filter(task => task.isDone);
        default:
          return this.tasks;
      }
    }
  },
  methods: {
    onDeleteTask(task) {
      this.$emit("deleteTask", task);
    },
    onToggleTask(task) {
      this.$emit("toggleTask", task);
    }
  }
};
</script>

<style scoped>
</style>