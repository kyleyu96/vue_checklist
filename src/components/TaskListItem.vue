<template>
  <v-row align="center" justify="space-between" class="list-item">
    <v-checkbox
      v-model="task.isDone"
      :label="task.name"
      hide-details
      class="checkbox"
      :class="{ done: task.isDone }"
    ></v-checkbox>
    <v-btn text icon color="red" @click="onDeleteTask" class="removeButton">
      <v-icon>clear</v-icon>
    </v-btn>
  </v-row>
</template>

<script>
export default {
  name: "TaskListItem",
  props: ["task"],
  methods: {
    onDeleteTask() {
      this.$emit("deleteTask", this.task);
    }
  }
};
</script>

<style scoped>
.list-item {
  margin: 0 !important;
}
.removeButton {
  visibility: hidden;
}
.list-item:hover .removeButton {
  visibility: visible;
}
.checkbox {
  margin: 0;
  padding: 0;
}
.done {
  text-decoration: line-through;
}
</style>
