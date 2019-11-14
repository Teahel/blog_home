<template>
  <div class="hello" >

    <el-container height=80% direction="vertical">
      <el-header>Header</el-header>
      <el-container height="100%">
        <el-aside width="200px">
          <el-button type="danger" @click="show">危险按钮</el-button>
        </el-aside>
        <el-container >
          <el-main >
            <el-table
              :data="tableData"
              stripe
              style="width: 100%">
              <el-table-column
                prop="title"
                label="标题"
                width="180">
              </el-table-column>
              <el-table-column
                prop="content"
                label="内容"
                width="180">
              </el-table-column>
              <el-table-column
                prop="reprintlink"
                label="连接">
              </el-table-column>
            </el-table>

          </el-main>
          <el-footer>Footer</el-footer>
        </el-container>
      </el-container>
    </el-container>


  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
        tableData:[],
    }
  },
    methods:{
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
        show:function () {
            let datas = this;
            this.$axios.post("http://39.108.125.164:8080/core_start/article/findList") .then(function (response) {
                if(response.data!=null){
                    console.log(response.data.list);
                    datas.tableData = response.data.list;
                }
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
    height: 200px;

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
    height:100%;
    padding:0;
    margin:0;
    width:100%;
    margin-bottom: 5px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }


</style>
