<template>
  <h1>Reaction Timer</h1>
  <button @click="play" :disabled="isPlaying">play</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame" />
  <Result :score="score" v-if="showResults"/>
</template>

<script>

import Block from "@/components/Block";
import Result from "@/components/Result";

export default {
  name: 'App',
  components:{Block , Result},
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResults: false
    }
  },
  methods: {
    play(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  },
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
button{
  margin: 10px 10px;
  background: #029d87;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  text-align: center;
  font-size: 15px;
  color: white;
}

button:disabled,
button[disabled]{
  border: none;
  background-color: #029d87;
  opacity: 0.5;
  color: #e2e2e2;
}
</style>
