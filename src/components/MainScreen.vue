<template>
  <div class="screen">
    <h1>Pokémon's Memories</h1>
    <h3>Select mode to start game</h3>
    <div class="mode">
      <button @click="onStart(16)">
        <span>4x4</span>
        <span>Easy</span>
      </button>
      <button @click="onStart(36)">
        <span>6x6</span>
        <span>Noraml</span>
      </button>
      <button @click="onStart(64)">
        <span>8x8</span>
        <span>Hard</span>
      </button>
      <button @click="onStart(100)">
        <span>10x10</span>
        <span>Super Hard</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onStart (totalOfBlocks) {
      this.$emit("onStart", { totalOfBlocks });
    }
  }
}
</script>

<style scoped>
.mode {
  display: flex;
  margin-top: 2rem;
}
.mode button {
  font: var(--font);
  width: 150px;
  height: 150px;
  background: transparent;
  box-shadow: none;
  border: 1px solid var(--light);
  color: var(--light);
  display: flex;
  flex-direction: column;
  border-radius: 1rem;
  margin: 0 1rem;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}
.mode button:hover {
  background-color: var(--light);
  color: var(--dark);
}
.mode button span:first-child {
  font-size: 2rem;
}
.mode button span:last-child {
  display: block;
  font-size: 1.25rem;
  margin-top: 0.5rem;
}
</style>