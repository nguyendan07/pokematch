<template>
  <div class="screen">
    <h1>✨ Congratulations ✨</h1>
    <h2>{{ Math.round(timer / 1000) }} seconds</h2>
    <button @click="onStartAgain">Start Again</button>
  </div>
</template>

<script>
export default {
  props: {
    timer: {
      type: Number,
      require: true
    }
  },
  methods: {
    onStartAgain() {
      this.$emit("onStartAgain");
    }
  }
}
</script>

<style scoped>
.screen h2 {
  font-size: 3rem;
}
.screen button {
  font: var(--font);
  background: transparent;
  box-shadow: none;
  border: 1px solid var(--light);
  color: var(--light);
  margin: 1rem;
  padding: 1rem 1.25rem;
  border-radius: 0.5rem;
  font-size: 1.25rem;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}
.screen button:hover {
  background-color: var(--light);
  color: var(--dark);
}
</style>