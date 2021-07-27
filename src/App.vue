<template>
  <div>
    <Header></Header>
    <Tasks :tasks="tasks" @delete-task="onDelete"></Tasks>
    <AddTask @add-task="onAdd"></AddTask>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    onDelete(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    onAdd(title) {
      const newTask = {
        title,
        id: this.tasks.length,
      };
      this.tasks.push(newTask);
    },
  },

  create() {
    console.log("created");
  },
};
</script>

<style></style>
