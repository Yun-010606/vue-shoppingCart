<template>
  <div class="my-header" :style="{background, color}">{{title}}</div>
</template>

<script>
export default {
  // props可以是一个数组也可以是个对象
  // 对象：{props:属性名：value}
  // value 可以是个类型 也可以是个对象
  // value是对象的话 {默认值default:'', 数据类型type:类型, 是否必须要required：true/false}
  props: {
    title: String,
    background: {
      type: String,
      default: 'skyblue'
    },
    color: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="less" scoped>
.my-header {
  height: 45px;
  line-height: 45px;
  text-align: center;
  background-color: #1d7bff;
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 2;
}
</style>
