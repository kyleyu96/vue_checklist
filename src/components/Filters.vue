<template>
  <v-card-actions>
    <v-btn-toggle @change="onFilterChange" :value="filter" tile group>
      <v-btn value="all">All</v-btn>
      <v-btn value="active">Active</v-btn>
      <v-btn value="done">Completed</v-btn>
    </v-btn-toggle>
  </v-card-actions>
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
