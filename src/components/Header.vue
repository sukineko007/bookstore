<template>
    <el-menu
    :default-active="activeIndex2"
    class="el-menu-header"
    mode="horizontal"
    @select="handleSelect"
    background-color="darkolivegreen"
    text-color="#fff"
    active-text-color="#ffd04b">
        <div id="title" v-if="showFlag2">
          <img src="../assets/head.jpg" alt="logo.jpg">网上书店1.0
        </div>
        <div id="title2" v-if="showFlag1">
        <img src="../assets/head.jpg" alt="logo.jpg">网上书店后台管理系统
        </div>
      <div class="div2">
        <el-button type="danger"  @click="tuichu">退出登录</el-button>
      </div>
    </el-menu>
</template>

<script>
    import bus from './BUS.vue'

    export default {
    data() {
      return {
        showFlag1:false,
        showFlag2:false,
        activeIndex: '1',
        activeIndex2: '1',
      };
    },
    methods: {
      tuichu(){
        sessionStorage.clear();
        window.location = "/";
      }
    },
      mounted(){
        var userJsonStr = sessionStorage.getItem('userInfo');
        if (JSON.parse(userJsonStr).qq == 1){
          this.showFlag2 = true;
        }
        else {
          this.showFlag1 = true;
        }
      }
  }
</script>

<style scoped>
  .div2{
    float: right;
    margin-right: 30px;
    margin-top: 10px;
  }
   a:link {
     text-decoration: none;
   }
   a{
     font-size: 20px;
     color: black;
   }
   .el-menu-header{
       width: 100%;
     height: 7%;
       float:right;
   }

   img{
     height: 40px;
     width: 40px;
     border-radius:50px;
   }
   #title{
       height: 60px;
       line-height: 60px;
       font-size: 28px;
       float: left;
       color: aqua;
       margin-left: 30px;
   }
   #title2{
     height: 60px;
     line-height: 60px;
     font-size: 28px;
     float: left;
     color: aqua;
     margin-left: 30px;
   }

   #notice{
       float: right;
       margin-right: 60px;
       margin-top: 10px;

   }
</style>

