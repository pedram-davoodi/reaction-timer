<template>
  <div class="block" @click="stopTimer" v-if="showBlock">
    Click Me
  </div>
</template>

<script>
export default {
  name: "Block",
  props:['delay'],
  data(){
    return{
      'showBlock': false,
      'timer': null,
      'reactionTime': 0,
    }
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer(){
      clearInterval( this.time)
      this.$emit('end' , this.reactionTime);
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    } , this.delay)
  }
}
</script>

<style scoped>
  .block{
    width: 400px;
    background: #029d87;
    color: white;
    margin: auto auto;
    border-radius: 10px;
    padding: 100px 0;
    text-align: center;
    cursor: pointer;
  }
  div{
    font-weight: bold;
  }
</style>