<template>
  <div class="dialog__wrapper" v-if="visible" @click.self="close">
    <div class="dialog" :style="{width: width}">
      <div class="dialog__header">
        <slot name="title">
          <span class="dialog__title">{{ title }}</span>
        </slot>
        <button class="dialog__headerbtn" @click="close">X</button>
      </div>
      <div class="dialog__body">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'simpleDialog',
  data() {
    return {}
  },
  props: {
    title: {
      type: String,
      default: "提示",
    },
    visible: {
      type: Boolean,
      default: false
    },
    width: {
      type: String,
      default: "30%"
    }
  },
  methods: {
    close() {
      this.$emit('update:visible',false);
    },
  }
}
</script>

<style scoped>
  .dialog__wrapper {
    background: rgba(0,0,0, 0.8);
    position: fixed;
    z-index: 200;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-content: center;
    justify-content: space-evenly;
    flex-wrap: wrap;
  }
  .dialog {
    background: white;
    width: 40%;
    height: 50%;
    z-index: 300;
    border-radius: 10px;
  }
  .dialog__header {
    height: auto;
    padding-top: 5px;
    display: flex;
    align-content: flex-start;
    position: relative;
    justify-content: space-around;
  }
  .dialog__headerbtn {
    position: absolute;
    right: 5px;
    cursor: pointer;
    border: none;
    background: none;
    outline: none;
    font-size: 17px;
  }
  .dialog__body {
    height: 65%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
