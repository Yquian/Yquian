<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <HelloWorld/> -->
    <div class="dialog">
      <button @click="visible = true">打开弹窗</button>

      <simple-dialog 
          :visible.sync="visible"
          :width="width"
          :title="title"
          @close="onClose"
          @open="onOpen">
        <template v-slot:title>
          <div>⾃定义标题</div>
        </template>
        <template>
          <div>主体内容，随便写点什么...</div>
        </template>
      </simple-dialog>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import simpleDialog from './components/simpleDialog.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    simpleDialog
  },
  data() {
    return {
      visible: false,
      width: '50%',
      title: ""
    };
  },
  methods: {
    onClose() {
      console.log("关闭弹窗回调")
    },
    onOpen() {
      console.log("打开弹窗回调")
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
