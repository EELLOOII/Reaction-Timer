<template>
  <div>
    <h1>{{ title }}</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <!-- <p v-if="showResults">Reaction time: {{ score }} ms</p> -->
    <Results v-if="showResults" :score="score"/>
  </div>   
</template>

<script>

import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: "App",
  components: { Block, Results },

  data() {
    return {
      title: "Reaction Timer Game",
      isPlaying: false,
      delay: null,
      score: null,
      showResults : false
    };
  },
  methods: {
    start() {
      this.showResults = false
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
    },
    endGame(reactionTime) {
      this.showResults = true
      this.score = reactionTime 
      this.isPlaying = false
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
