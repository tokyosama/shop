<template>
  <div id="app">
      <div class="jumbotron">
          <h1 class="display-4">微博热搜榜</h1>
          <p class="lead"> 当前微博热搜:{{time}}</p>
          <hr class="my-4">
          <button type="button" class="btn btn-primary btn-lg" @click="look">{{text}}</button>
          <wb-hot v-for="item in data" 
          :key="item.index" 
          :title="item.title" 
          :hot="item.hot" 
          :url="item.url"
          :time="item.time"
          @click.native="goto(item)" v-show="flag"></wb-hot>  
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
      time:'',
      flag:false,
      text:'点击查看'

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
      this.time=res.time
      this.data=res.data
      // console.log(this.data)
      
    },
    look(){
      this.flag=!this.flag
      if(this.flag){
        this.text='点击隐藏'
      }
      else{
        this.text='点击查看'

      }

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
