<template>
  <div class="page">
      <h1>这是模板里的内容</h1>
      {{mydatas}}
  <div>
    <button @click="add">点击{{count}}数</button>
    <h2></h2>
  </div>
  <!-- 卡槽 -->
  <div class="container">
    <header>
      <slot name="header"></slot>
    </header>
    <main>
      <slot></slot>
    </main>
    <footer>
      <slot name="footer"></slot>
    </footer>
  </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props:['mydatas'],
  data() {
    return {
      count:0
    }
  },
  components: {

  },
  methods:{
    add(){
      this.count++;
      this.$emit('setCountNumber',this.count)
    }
  }
}
</script>

<style scoped lang="scss">
</style>