<template>
  <div>
    <button type="button" @click="onFilterChange('all')">All</button>
    <button type="button" @click="onFilterChange('active')">Active</button>
    <button type="button" @click="onFilterChange('done')">Completed</button>
  </div>
</template>

<script>
export default {
  name: "Filters",
  props: ["filter"],
  methods: {
    onFilterChange(newFilter) {
      this.$emit("filterChange", newFilter);
    }
  }
};
</script>

<style scoped>
</style>