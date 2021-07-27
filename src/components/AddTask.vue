<template>
  <form class="form">
    <p>Enter Task Title:</p>
    <input type="text" placeholder="Enter Task Title" v-model="title" />
    <Button Text="Add Task" Color="skyBlue" @click="addTask($event)"></Button>
  </form>
</template>

<script>
import Button from "./Button";
export default {
  name: "AddTask",
  components: {
    Button,
  },
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTask(e) {
      e.preventDefault();
      this.title.length ? this.$emit("add-task", this.title) : "";
      this.title = "";
    },
  },
  emits: ["add-task"],
};
</script>

<style scoped>
.form {
  display: flex;
  justify-content: center;
  align-items: center;
}
.form > p {
  font-size: 20px;
  padding: 0 2rem;
}
.form input {
  height: 2rem;
  width: 15rem;
}
</style>
