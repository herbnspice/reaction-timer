<template>

  <h1>Ninja Reaction Timer</h1>
  <Block :delay="delay" v-if="isPlaying" @endGame="endGame"></Block>
  <button @click="start" :disabled="isPlaying" > Play</button>
  <Results :score="score" v-show="showResult" > </Results>
</template>

<script>
import Block from './components/Block'

import Results from './components/Results'
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying : false,
      showResult: false,
      delay: 100,
      score: 0,
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 2000
      this.isPlaying = true 
      this.showResult = false
      console.log( this.delay)
    },
    endGame( reactionTimer ){
      this.score = reactionTimer 
      this.isPlaying = false
      this.showResult = true
      console.log( 'end' , this.score )
    }
  },
  update(){
    console.log( 1)
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
button{
  border: solid #000 thin;
  background: #f3f3f3;
  font-size: 20px;
  color: #000;
  padding:10px 40px;
  border-radius: 6px;
}
</style>
