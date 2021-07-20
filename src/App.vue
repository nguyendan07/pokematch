<template>
  <main-screen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"></main-screen>
  <interact-screen v-if="statusMatch === 'match'"></interact-screen>
</template>

// <script setup>
// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/master/active-rfcs/0040-script-setup.md
// </script>
<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from './components/InteractScreen.vue';
export default {
  components: { MainScreen, InteractScreen },
  name: "App",
  data () {
    return {
      statusMatch: "default",
    };
  },
  methods: {
    onHandleBeforeStart (config) {
      this.statusMatch = "match";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
