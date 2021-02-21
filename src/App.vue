<template>
  <h1>Reaction Timer</h1>
  <button @click="startSession" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endSession"/>
  <Result v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/Block'
import Result from './components/Result'

export default {
  name: 'App',
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    }
  },
  methods: {
    startSession() {
      var minimumDelay = 300
      var maximumDelay = 5000
      this.delay = Math.floor(Math.random() * (maximumDelay - minimumDelay) + minimumDelay)
      this.isPlaying = true
      this.showResult = false
    },
    endSession(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    },
  }
}
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

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
