<template>
 <h1>Reaction Time Calculator</h1>
 
 <div class="instruction" v-if="!showResult">
    <h4>Instructions</h4>
      <ul>
        <li>After clicking on the <b>Start</b> button a blue squre block will appear within a random time period.</li>
         <li>Click on that as soon as it appears to measure your reaction time.</li>
      </ul>
 </div>
 
 <button @click="startGame" :disabled="isPlaying">Start</button>
 
 <Block v-if="isPlaying" :delay="delay" @endGame="endGame"/>
 
 <Result v-if="showResult" :score="reactTime" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',

  components: {
    Block,
    Result
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      reactTime: null,
      showResult: false
    }
  },

  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
      console.log(this.delay)
    },

    endGame(reactionTime) {
         this.isPlaying = false,
         this.reactTime = reactionTime
         this.showResult = true

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
  color: #444;
  margin-top: 60px;
}
</style>
