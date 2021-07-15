<template>
  <div
    @click="toggleRemainder()"
    :class="[task.remainder ? 'remainder' : '', 'task']"
  >
    <div>
      <h4>
        {{ task.title }}
        <font-awesome-icon
        @click="handleDelete(task.id)"
        class="delete-icon"
        :icon="deleteIcom"
      />
      </h4>
      <p>{{ task.date }}</p>
    </div>

  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTimes } from "@fortawesome/free-solid-svg-icons";

export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    toggleRemainder() {
      this.task.remainder = !this.task.remainder;
    },
    handleDelete(id) {
      this.$emit("delete-item", id);
    },
  },
  data() {
    return {
      deleteIcom: faTimes,
    };
  },

  components: {
    FontAwesomeIcon,
  },
};
</script>

<style scoped>
.task {
  background-color: #ddd;
  margin: 10px;
  padding: 5px;
  line-height: 3px;
  padding-left: 10px;
  cursor: pointer;
  box-sizing: border-box;

}
.remainder {
  border-left: 5px solid orangered;
}
.delete-icon {
  color: red;
  margin-left: 400px;
  font-size: 20px;
  transition: 0.3s;
}
</style>
