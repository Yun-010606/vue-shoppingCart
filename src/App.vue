<template>
  <div class="app">
    <MyHeader title="Shopping Cart" color="pink"></MyHeader>
    <MyGoods></MyGoods>
    <MyFooter></MyFooter>
  </div>
</template>

<script>
import MyHeader from '#/MyHeader'
import MyGoods from '#/MyGoods'
import MyFooter from '#/MyFooter'
export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  }
}
</script>

<style scoped>
.app {
  padding: 50px 0;
}
</style>
