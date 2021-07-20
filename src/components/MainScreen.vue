<template>
  <div class="screen">
    <h1>Pokémon's Memories</h1>
    <h3>Select mode to start game</h3>
    <div class="action">
      <button @click="onStart(4)">
        <span>4x4</span>
        <span>Easy</span>
      </button>
      <button @click="onStart(6)">
        <span>6x6</span>
        <span>Noraml</span>
      </button>
      <button @click="onStart(8)">
        <span>8x8</span>
        <span>Hard</span>
      </button>
      <button @click="onStart(10)">
        <span>10x10</span>
        <span>Super Hard</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onStart (mode) {
      this.$emit("onStart", { mode });
    }
  }
}
</script>