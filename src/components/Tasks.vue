<template>
  <div v-for="task in tasks" :key="task.id" class="task">
    <h1 v-if="!(edit && task.id === id)">
      Title:
      <span :class="task.isCompleted ? 'completed' : 'not-completed'">
        {{ task.title }}
      </span>
    </h1>
    <input v-else type="text" v-model="task.title" />
    <div>
      <Button
        v-if="edit && task.id === id && !task.isCompleted"
        Text="Save"
        Color="green"
        @click="onSave(task.id, task.title)"
      ></Button>
      <Button
        v-if="edit && task.id === id && !task.isCompleted"
        Text="Back"
        Color="orange"
        @click="onBack()"
      ></Button>
      <Button
        v-else
        v-show="!task.isCompleted"
        Text="Edit"
        Color="orange"
        @click="onEdit(task.id)"
      ></Button>
      <Button
        v-show="!edit"
        :Text="!task.isCompleted ? 'Completed?' : 'Not Completed?'"
        :Color="!task.isCompleted ? 'green' : 'red'"
        @click="toggleCompleted(task.id)"
      ></Button>
      <Button Text="Delete" Color="red" @click="onDelete(task.id)"></Button>
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  data() {
    return {
      edit: false,
      id: null,
    };
  },
  components: {
    Button,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
    onEdit(id) {
      (this.id = id), (this.edit = true);
    },
    onBack() {
      this.edit = false;
    },
    onSave(id, title) {
      title.length ? this.$emit("edit-task", id, title) : "";
      this.edit = false;
    },
    toggleCompleted(id) {
      console.log(id);
      this.$emit("toggle-completed", id);
    },
  },
  emits: ["delete-task", "edit-task", "toggle-completed"],
};
</script>

<style scoped>
.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.5rem 0;
  background-color: #f7f7f7;
  padding: 0 10rem;
}
input {
  margin: 1rem;
  height: 2rem;
  width: 15rem;
}
.completed {
  text-decoration: line-through;
}
.not-completed {
  text-decoration: none;
}
</style>
