<template>
  <div class="app-container">
    <Herader :showAddTask="showAddTask" @addTask-toggle="handleToggle"  />
    <div v-if="showAddTask">
      <Add-task  @add-task="addTaskHandler" />
    </div>
    <Tasks @delete-item="deleteHandler" :tasks="tasks" />
  </div>
</template>

<script>
import AddTask from "./components/AddTask/AddTask.vue";
import Herader from "./components/Header/Herader.vue";
import Tasks from "./components/Tasks/Tasks.vue";
export default {
  components: { Herader, Tasks, AddTask },

  data() {
    return {
      tasks: [],
      showAddTask:false,
    };

  },
  methods: {
    addTaskHandler(task) {
      this.tasks = [...this.tasks, task];
    },

    deleteHandler(id) {
      if (confirm("Are you sure you will delete task")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    handleToggle(){
      this.showAddTask = !this.showAddTask;
    }
  },

  created() {
    this.tasks = [
      {
        id: "1",
        title: "Doctors Appointment",
        date: "March 5th at 2:30pm",
        remainder: false,
      },
      {
        id: "2",
        title: "Metting at Schook",
        date: "March 5th at 5:30pm",
        remainder: false,
      },
      {
        id: "3",
        title: "Bazr Appointment",
        date: "March 5th at 12:30pm",
        remainder: true,
      },
      {
        id: "4",
        title: "Mina Bazar Appointment",
        date: "March 5th at 11:30pm",
        remainder: false,
      },
    ];
  },
};
</script>

<style scoped>
* {
  margin: 0px;
  padding: 0px;
  font-family: Arial, Helvetica, sans-serif;
}
.app-container {
  border: 1px solid rgb(230, 218, 218);
  padding: 20px;
  width: 40%;
  margin: auto;
  border-radius: 5px;
  margin-top: 40px;
}
</style>
