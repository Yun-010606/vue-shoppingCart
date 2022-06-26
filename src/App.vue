<template>
  <div class="app">
    <MyHeader title="Shopping Cart" color="pink"></MyHeader>
    <MyGoods v-for="item in goodList" :key="item.goods_id"
    :goods="item"
    ></MyGoods>
    <MyFooter></MyFooter>
  </div>
</template>

<script>
import MyHeader from '#/MyHeader'
import MyGoods from '#/MyGoods'
import MyFooter from '#/MyFooter'
// 引入axios
import axios from 'axios'
export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data () {
    return {
      goodList: []
    }
  },
  created () {
    this.getGoods()
  },
  methods: {
    async getGoods () {
      const res = await axios({
        url: '/api/cart'
      })
      // console.log(res.data.list)
      this.goodList = res.data.list
    }
  }
}
</script>

<style scoped>
.app {
  padding: 50px 0;
}
</style>
