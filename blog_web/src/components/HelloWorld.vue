<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{show}}</h2>
    <h3>{{count()}}</h3>
    <div v-html="message"></div>
    {{1+10}}<br>
    {{ok?'YES':'NO'}}<br>
    {{message.split('').reverse().join("")}}

    <div v-bind:id="'list-'+id">测试教程</div>
    <p  v-if="seen">现在你看到我了！</p>
    <pre><a v-bind:href="url">gitee.com</a></pre>
    <h6>    <a v-on:click="doSomething">点击事件</a>    </h6>

    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>


  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
        msg: 'Welcome to Your Vue.js App',
        show:'kiahis',
        ok:true,
        message:'li.teahel@gmail.com',
        id:1,
        seen:false,
        url:'https://gitee.com'
    }
  },
    methods:{
        count:function(){
          return this.show +" - 测试的世界真是美滋滋"
        },
        doSomething:function () {
           return  this.$axios.get("http://39.108.125.164:8080/core_start/user/login",{params:{username:'matthew',password:'1996'}}) .then(function (response) {
               if(response.data!=null){
                 alert(response.data.msg+"  "+response.data.code);
               }
               console.log(response);
            })
                .catch(function (error) {
                    console.log(error);
                });
        }
    }
}
</script>

<style scoped>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
