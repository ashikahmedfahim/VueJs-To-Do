<template>
  <div v-for="task in tasks" :key="task.id" class="task">
    <h1>{{ task.title }}</h1>
    <Button Text="Delete" Color="red" @click="onDelete(task.id)"></Button>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Button,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
  },
  emits: ["delete-task"],
};
</script>

<style scoped>
.task {
  background-color: #f7f7f7;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0.5rem 0;
}
</style>
