<template>
  <div id="app">
      <div class="jumbotron">
          <h1 class="display-4">微博热搜榜</h1>
          <p class="lead"> 调用API查看当前微博热搜</p>
          <hr class="my-4">
          <!-- <button type="button" class="btn btn-primary btn-lg" @click="look">点击查看</button> -->
          <wb-hot v-for="item in data" 
          :key="item.index" 
          :title="item.title" 
          :hot="item.hot" 
          :url="item.url"
          :time="item.time"
          @click.native="goto(item)"></wb-hot>  
        </div>

  </div>
</template>

<script>
import WbHot from './components/WbHot/WbHot.vue'
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return {
      data:[],

    }
  },
  components: {
    WbHot
  },
  beforeCreate(){


  },
  created(){
    this.getList()

  },
  methods:{
     async getList(){
      const {data:res} = await axios.get('https://api.vvhan.com/api/wbhot')
      if(!res.success) return alert('sb')
      this.data=res.data
      // console.log(this.data)
      
    },
    look(){

    },
    goto(parms){
      window.open(parms.url)
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
</style>
