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
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      getId:"",
      getUser:""
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
    }
  },
   beforeRouteUpdate(to, from, next) {
    //在当前路由改变，但是该组件被复用时调用
    //对于一个带有动态参数的路径 /good/:id，在 /good/1 和 /good/2 之间跳转的时候，
    // 由于会渲染同样的good组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
    console.log(this, 'beforeRouteUpdate'); //当前组件实例
    console.log(to, '组件独享守卫beforeRouteUpdate第一个参数');
    console.log(from, '组件独享守beforeRouteUpdate卫第二个参数');
    console.log(next, '组件独享守beforeRouteUpdate卫第三个参数');
    next();
  },
  //监听路由
   watch: {
    $route: {
      handler: function(route) {
        console.log(route.params)
      },
      immediate: true
    }
  },
}
</script>
