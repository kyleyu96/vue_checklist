<template>
  <v-form @submit="onAddTask">
    <v-text-field
      v-model="userInput"
      placeholder="Add a new task"
      clearable
      full-width
      outlined
      prepend-inner-icon="edit"
      rounded
      hide-details
    />
  </v-form>
</template>

<script>
export default {
  name: "NewTask",
  data() {
    return { userInput: "" };
  },
  methods: {
    onAddTask(event) {
      event.preventDefault();
      const trimmed = this.userInput.trim();
      if (trimmed !== "") {
        this.$emit("addTask", trimmed);
      }
      this.userInput = "";
    }
  }
};
</script>
