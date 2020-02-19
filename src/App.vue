<template>
  <v-app>
    <v-content>
      <v-container fluid class="app-container">
        <v-row align="start" justify="center">
          <v-col cols="12" sm="10" md="6">
            <v-card class="elevation-12">
              <v-toolbar color="primary" dark flat>
                <v-spacer></v-spacer>
                <v-toolbar-title>Checklist</v-toolbar-title>
                <v-spacer></v-spacer>
              </v-toolbar>
              <v-card-text>
                <NewTask @addTask="onAddTask" />
                <TaskList
                  :tasks="tasks"
                  :filter="filter"
                  @deleteTask="onDeleteTask"
                />
              </v-card-text>
              <Filters :filter="filter" @filterChange="onFilterChange" />
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
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
    }
  }
};
</script>

<style scoped>
.app-container {
  padding: 15vh 0;
}
</style>
