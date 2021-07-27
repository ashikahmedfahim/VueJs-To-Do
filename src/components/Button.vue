<template>
  <button @click="onClick()" :style="{ background: Color }" class="button">
    {{ Text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    Text: String,
    Color: String,
  },
  methods: {
    onClick() {
      
    },
  },
};
</script>

<style scoped>
.button {
  height: 2.5rem;
  width: 7rem;
  border: none;
  color: white;
  border-radius: 5px;
  margin: 0 2rem;
}

</style>
