<template>
  <div class="hello">

    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>卡片名称</span>
        <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
      </div>
      <div v-for="o in 4" :key="o" class="text item">
        {{'列表内容 ' + o }}
      </div>
    </el-card>

  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {

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
        },

    },
    created() {
       this.$axios.get("http://39.108.125.164:8080/core_start/user/login",{params:{username:'matthew',password:'1996'}}) .then(function (response) {
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
</script>

<style scoped>
  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 480px;
  }
</style>
