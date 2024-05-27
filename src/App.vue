<template>
  <div class="theme">
    <h1>Aymen reaction timer game!</h1>
    <button class="show-scores" @click="showScores" >Show scores</button>
    <button class="start" @click="start" :disabled="isPlaying">Start</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" /> 
    <Modal v-show="showModal" @close="close" :tryies="tryies" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
import Modal from './components/Modal.vue'
import './assets/global.css'
export default {
  name: 'App',
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false,
      tryies:[],
      showModal: false
    }
  },
  components: {
    Block,
    Results,
    Modal
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.tryies.push(this.score)
      this.isPlaying = false;
      this.showResults = true
    },
    showScores(){
      this.showModal = true
    },
    close(){
      this.showModal = false
    }
  }
}
</script>

<style>
@media (prefers-color-scheme: dark) {
  .theme {
    background: #444;
    color: #bcd;
    min-height: 100vh;
  }
}
@media (prefers-color-scheme: light) {
  .theme {
    background: #bcd;
    color: #444;
    min-height: 100vh;
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
}
button.start{
  background:#2453fe;
  color:white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 20px;
}
button.show-scores{
  background:lightgreen;
  color:#444;
  font-weight: 600;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 20px;
}
h1{
  margin: 0
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
