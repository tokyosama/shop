<template>
  <div id="app">
    <input type="text" v-model="num">
    <button type="button" @click="num+=3">经验+3</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      num:0

    }
  },
  components: {
    
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
</style>
