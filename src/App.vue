<template>
  <v-app>
    <h1>Checklist</h1>
    <NewTask @addTask="onAddTask" />
    <TaskList
      :tasks="tasks"
      :filter="filter"
      @deleteTask="onDeleteTask"
      @toggleTask="onToggleTask"
    />
    <Filters :filter="filter" @filterChange="onFilterChange" />
  </v-app>
</template>

<script>
import NewTask from "./components/NewTask";
import TaskList from "./components/TaskList";
import Filters from "./components/Filters";

export default {
  name: "App",
  components: {
    NewTask,
    TaskList,
    Filters
  },
  data() {
    return { tasks: [], filter: "all" };
  },
  methods: {
    onFilterChange(filter) {
      this.filter = filter;
    },
    onAddTask(task) {
      this.tasks.push({
        name: task,
        isDone: false
      });
    },
    onDeleteTask(task) {
      const index = this.tasks.findIndex(t => t === task);
      this.tasks.splice(index, 1);
    },
    onToggleTask(task) {
      task.isDone = !task.isDone;
    }
  }
};
</script>
