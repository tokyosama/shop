<template>
  <div class="hello" style="background-color: #eeffff">
    <div class="list-group">
      <div class="list-group-item list-group-item-action">
        <div class="d-flex w-100 justify-content-between">
          <h5 class="mb-1 t"><span style="color:#f26d5f ">{{indexs}}</span>：{{title}}</h5>
        </div>
        <span class="badge badge-success badge-pill hot">热度:{{hot}}</span>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'WbHot',

    props: {
      indexs:{
        type:Number,
        default:0
      },
      title: {
        type: String,
        default: ''
      },
      hot: {
        type: String,
        default: ''
      },
      url: {
        type: String,
        default: ''
      },
      time: {
        type: String,
        default: '00:00:00'
      }
    },
    methods: {

    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .urlSize {
    font-size: 1px
      /* margin-left:0 */
  }

  .badge {
    line-height: 1.8
  }

  .t {
    text-align: left
  }

  .hot {
    float: right;
  }
</style>