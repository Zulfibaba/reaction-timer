<template>
  <div class="main">
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>

    <block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" />
  </div>
</template>

<script>
import block from "./components/block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },

    endGame(reactionTimer) {
      this.score = reactionTimer;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
body{
  margin: 0;
}
.main{
  margin: 0;
  height: 99vh;
  background-color: rgb(14, 3, 42); 
  padding: 60px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0faf87;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
