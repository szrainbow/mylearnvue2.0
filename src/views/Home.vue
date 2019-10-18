<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1 @click="getvserve">{{welcomes}}</h1>
    <my-vue />
    <!-- <HelloWorld :msg="welcomes"/> -->
    <!-- 双向绑定 -->
    <h1>{{messages}}</h1>
    <input type="text" v-model="messages">
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import MyVue from '@/components/myvue.vue'
export default {
  name: 'home',
  components: {
    HelloWorld,
    MyVue
  },
  data(){
    return{
      welcomes:"this content is pull from github git",
      messages:"hello world!"
    }
  },
  methods: {
    getvserve(){
      this.welcomes=this.welcomes.split("").reverse().join("")
    }
  }
}
</script>
