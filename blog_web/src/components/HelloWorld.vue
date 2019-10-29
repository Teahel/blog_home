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
    {{message|Utest}}


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
            return this.seen=true
        },
        Utest:function (value) {
            if(!value){
                return ''
            }
            value = value.toString()
            return value.charAt(0).toUpperCase()+value.slice(1)
        }
    }
}
</script>

