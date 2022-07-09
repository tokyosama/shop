<template>
  <div id="app">
    <div class="jumbotron">
      <!-- <h1 class="display-4">微博热搜榜</h1> -->
      <img src="https://simg.s.weibo.com/20210521_hot_banner_h5.png" alt="" style="width: 100%;">
      <p class="lead"> 当前微博热搜:{{time}}</p>
      <div>
        <img src="https://h5.sinaimg.cn/m/weibo-lite/img/pwalogo.417d1674.svg" alt="" style="width: 30px;height: 30px;">
        实时热点，每分钟更新一次捏
      </div>
      <hr>
      <button type="button" class="btn btn-primary btn-lg check" @click="look">{{text}}</button>
      <button type="button" class="btn btn-primary refresh mb-1" @click="refresh">刷新</button>
      <wb-hot v-for="(item,index) in data" :key="index" :indexs="index+1" :title="item.title" :hot="item.hot" :url="item.url"
        :time="item.time" @click.native="goto(item)" v-show="flag"></wb-hot>
    </div>

  </div>
</template>

<script>
  import WbHot from './components/WbHot/WbHot.vue'
  import axios from 'axios'
  export default {
    name: 'App',
    data() {
      return {
        data: [],
        time: '',
        flag: false,
        text: '点击查看',
        index:'0'

      }
    },
    components: {
      WbHot
    },
    beforeCreate() {


    },
    created() {
      this.getList()

    },
    methods: {
      async getList() {
        const {
          data: res
        } = await axios.get('https://api.vvhan.com/api/wbhot')
        if (!res.success) return alert('sb')
        this.time = res.time
        this.data = res.data
        // console.log(this.data)

      },
      look() {
        this.flag = !this.flag
        if (this.flag) {
          this.text = '点击隐藏'
        } else {
          this.text = '点击查看'

        }

      },
      goto(parms) {
        window.open(parms.url)
      },
      refresh() {
        this.getList()

      }

    }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    /* margin-top: 0px; */
  }

  .display-4 {
    color: #ff8200
  }

  .refresh {
    float: right;
    width: 60px;
    height: 30px;
    font-size: 12px;
    text-align: center
  }
  .lead{
    font-size: 16px;
  }

  .check{
    height: 45px;
  }
</style>