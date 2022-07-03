<template>
  <div id="app">
    <span>我祝你能活</span>
    <span class="ml-2 mr-2">{{num}}</span>
    <span>岁</span>
    <hr>
    <button type="button" class="btn btn-primary" @click="rand">点击许愿</button>
    <hr>
    <button type="button" class="btn btn-success" @click="rands">太少</button>
    <hr>
    <span>您可以活</span>
    <input type="text" v-model="ages" class="put">
    <span>岁</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      num:0,
      ages:0

    }
  },
  components: {
    
  },
  methods:{
    rand(){
      let n = 20
      let m=60
      this.num = Math.floor(Math.random()*(m-n+1))+n
      return this.num
    },
      rands(){
      let n = 70
      let m=150
      this.ages = Math.floor(Math.random()*(m-n+1))+n
      return this.ages
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
  color: #2c3e50;
  margin-top: 60px;
}
.put{
  width: 40px;
}
</style>
