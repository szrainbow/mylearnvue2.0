<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>{{getUser}}</h2>
    <h2>{{getId}}</h2>
    <button @click="getRoute">获取动态路由</button>
    <!-- //模板语法，指令 -->
    <div>
      <div @click="click1">
        <div @click.stop="click2">
          这是一个例子
        </div>
      </div>
      <!-- style和class的绑定 -->
      <div
      v-bind:class="{active:isActive,test:isSelect}"
      style="height:200px;width:200px;font-size:30px;"
      >
        hello my boys
      </div>
      <!-- 监听 -->
      <button class="hello" @click="getnumber('abc',$event)">查看</button>
      <input v-on:keyup.enter="submit">
      <button @click.ctrl="onClick">A</button>

      <!-- 表单绑定 -->
      <input type="checkbox" value="page1" v-model="names" >
      <label >page1</label>
      <input type="checkbox" value="page2" v-model="names" >
      <label >page2</label>
      <input type="checkbox" value="page3" v-model="names" >
      <label >page3</label>
      <h1>{{names}}</h1>

      <div>
        <input type="radio" value="苹果" v-model="selectname">
        <label >page1</label>
        <input type="radio" value="香蕉" v-model="selectname">
        <label >page1</label>
        <h2>{{selectname}}</h2>
      </div>
      <my-vue :mydatas="moduledata" @setCountNumber="getCountNumber">
        <template v-slot:header>
          <h1>Here might be a page title</h1>
        </template>

        <p>A paragraph for the main content.</p>
        <p>And another one.</p>

        <template v-slot:footer>
          <p>Here's some contact info</p>
        </template>

      </my-vue>
    </div>
  </div>
</template>
<script>
import MyVue from "../components/myvue";
export default {
  components: {
    MyVue
  },
  data () {
    return {
      getId:"",
      getUser:"",
      isActive:true,
      isSelect:true,
      names:["page1","page2"],
      selectname:"苹果",
      moduledata:["1",'2',"3"]
    }
  },
  methods: {
    getRoute(){
      this.getUser=this.$route.params.username;
      this.getId=this.$route.params.post_id;
    },
     click1:function(){
      console.log("click1")
    },
    click2:function(){
      console.log("click2")
    },
    getnumber(str,e){
      console.log(str)
      console.log(e)
    },
    submit(){
      console.log("按下enter")
    },
    onClick(){
      console.log('按下ctrl键')
    },
    getCountNumber(e){
      console.log(e)
    }
  },
  //  beforeRouteUpdate(to, from, next) {
  //   //在当前路由改变，但是该组件被复用时调用
  //   //对于一个带有动态参数的路径 /good/:id，在 /good/1 和 /good/2 之间跳转的时候，
  //   // 由于会渲染同样的good组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
  //   // 可以访问组件实例 `this`
  //   console.log(this, 'beforeRouteUpdate'); //当前组件实例
  //   console.log(to, '组件独享守卫beforeRouteUpdate第一个参数');
  //   console.log(from, '组件独享守beforeRouteUpdate卫第二个参数');
  //   console.log(next, '组件独享守beforeRouteUpdate卫第三个参数');
  //   next();
  // },
  //监听路由
   watch: {
    $route: {
      handler: function(route) {
        console.log(route.params)
      },
      immediate: true
    },
  },
}
</script>
<style>
  .active{
    background:#f00
  }
  .test{
    color: #ff0
  }
</style>
