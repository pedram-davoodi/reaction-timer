<template>
  <div>
    <h1>Result : {{ score }} ms</h1>
    <p>{{prefix}} You're {{rate}}</p>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: ['score'],
  data(){
    return {
      'rate': null,
      'prefix': ""
    }
  },
  mounted() {
    if (this.score < 200){
      this.rate = 'fast'
      this.prefix = 'Wow!'
    }
    else if (this.score < 300){
      this.rate = 'slow'
      this.prefix = 'Oops!'
    }
    else{
      this.rate = 'too slow'
      this.prefix = 'Oh no!'
    }
  }
}
</script>

<style scoped>
  p{
    color: #029d87;
    font-weight: bold;
  }
</style>