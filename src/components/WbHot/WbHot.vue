<template>
    <div class="hello">
        <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action">
              <div class="d-flex w-100 justify-content-between">
                <h5 class="mb-1">{{title}}</h5>
                <span class="badge badge-primary badge-pill">热度:{{hot}}</span>
              </div>
            </a>
          </div>
  
    </div>
  </template>
  
  <script>
  export default {
    name: 'WbHot',
  
    props: {
      title:{
        type:String,
        default:''
      },
      hot:{
        type:String,
        default:''
      },
      url:{
        type:String,
        default:''
      },
      time:{
        type:String,
        default:'00:00:00'
      }
    },
    methods:{
  
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  .urlSize{
    font-size: 1px
    /* margin-left:0 */
  }
  .badge{
    line-height: 1.8
  }
  </style>
  