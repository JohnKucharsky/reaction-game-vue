<template>
  <h1>Reaction Timer</h1>
  <button @click="start">show delay</button>
  <BlockComponent v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsComponent v-if="showResults" :score="score" />
</template>

<script>
import BlockComponent from "./components/BlockComponent.vue";
import ResultsComponent from "./components/ResultsComponent.vue";
export default {
  name: "App",
  components: {
    BlockComponent,
    ResultsComponent,
  },
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
    endGame(rt) {
      this.score = rt;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  padding: 0.5rem 1rem;
  background: #fff;
  color: #444;
  border: 2px solid #444;
  border-color: #444;
  border-radius: 0.3rem;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.7);
  transition: all 0.2s linear;
}
button:hover {
  box-shadow: 2px 2px 7px rgba(0, 0, 0, 0.6);
  transform: scale(0.97);
}
button:focus {
  box-shadow: 2px 2px 7px rgba(0, 0, 0, 0.6);
  transform: scale(0.95);
}
</style>
