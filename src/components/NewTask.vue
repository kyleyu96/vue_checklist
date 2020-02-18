<template>
  <form @submit="onAddTask">
    <input type="text" v-model="userInput" placeholder="Add a new task" required />
  </form>
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

<style scoped>
</style>