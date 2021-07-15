<template>
  <div class="header-container ">
    <h1>Task Tracker</h1>
    <button
      :style="{ backgroundColor: [showAddTask ? 'red' : 'green'] }"
      @click="addTask"
      class="add-btn"
    >
      <span v-if="showAddTask">Close</span>
      <span v-else>Add Task</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    showAddTask: Boolean,
  },

  methods: {
    addTask() {
      this.$emit("addTask-toggle");
    },
  },
};
</script>

<style scoped>
.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}
button.add-btn {
  padding: 11px 10px;
  color: white;
  border-radius: 5px;
  border: 1px solid blue;
  cursor: pointer;
}
button.add-btn:hover {
  background-color: #6953e7;
  color: wheat;
}
</style>
