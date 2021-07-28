<template>
  <div>
    <Header></Header>
    <Tasks
      :tasks="tasks"
      @delete-task="onDelete"
      @edit-task="onEdit"
      @toggle-completed="onToggle"
    ></Tasks>
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
    onEdit(id, title) {
      this.tasks = this.tasks.map((task) => {
        task.id === id ? (task.title = title) : "";
        return task;
      });
    },
    onAdd(title) {
      const newTask = {
        title,
        isCompleted: false,
        id: this.tasks.length,
      };
      this.tasks.push(newTask);
    },
    onToggle(id) {
      this.tasks = this.tasks.map((task) => {
        task.id === id ? (task.isCompleted = !task.isCompleted) : "";
        return task;
      });
    },
  },
};
</script>

<style></style>
