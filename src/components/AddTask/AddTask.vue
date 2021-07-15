<template>
  <div class="form">
    <form @submit="handleSubmit" action="">
      <label for="text"> Task </label> <br />
      <input
        type="text"
        name="text"
        id=""
        placeholder="task"
        required
        v-model="title"
      /><br /><br />
      <label for="date">Date & Time</label><br />
      <input
        type="text"
        name="time"
        id=""
        placeholder="Date & time"
        required
        v-model="date"
      /><br /><br />
      <label for="checkbox">Set Remainder</label>
      <input type="checkbox" name="" id="" v-model="remainder"/><br><br>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      id:null,
      title: null,
      date:null,
      remainder: false,
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();

      const newTask = {
        id:Math.floor(Math.random()*1000),
        title: this.title,
        date: this.date,
        remainder: this.remainder,
      };

      this.$emit('add-task',newTask);
      console.log("add",newTask);
      
      this.title = '',
      this.date='',
      this.remainder=''
    },
  },
};
</script>

<style scoped>
input[type="text"] {
    width: 95%;
    border-radius: 5px;
    padding: 10px;
    background-color: #ddd;
    border: none;
}


input[type="submit"] {
    width: 95%;
    background-color: black;
    color: white;
    padding: 10px;
    border: navajowhite;
    border-radius: 5px;
    cursor: pointer;
}
</style>
