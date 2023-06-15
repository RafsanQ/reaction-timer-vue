<template>
  <h1>Reaction Timer</h1>
  <br>
  <button @click="play" :disabled="isPlaying">
    PLAY
  </button>
  <br>
  <Block v-if="isPlaying" :delay="delay" @endGame="end"></Block>
  
</template>


<script>
  import Block from './components/Block.vue'

  export default {
    name: 'App',
    components: {
      Block
    },

    data(){
      return {
        isPlaying: false,
        delay: null,
        score: null
      }
    },

    methods:{
      play(){
        this.delay = 2000 + Math.random()*5000
        this.isPlaying = true
      },
      end(reactionTime){
        this.score = reactionTime
        this.isPlaying = false
      }
    }
  }
</script>




<style scoped>

</style>
