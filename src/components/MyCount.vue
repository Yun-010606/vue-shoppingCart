<template>
  <div class="my-counter">
    <button type="button" class="btn btn-light" @click="goods.goods_count--">-</button>
    <input type="number" class="form-control inp" v-model="goods.goods_count"/>
    <button type="button" class="btn btn-light" @click="goods.goods_count++">+</button>
  </div>
</template>

<script>
// 目标: 商品数量 - 控制
// 1. 外部传入数据对象
// 2. v-model关联对象的goods_count属性和输入框 (双向绑定)
// 3. 商品按钮 +和-, 商品数量最少1件
// 4. 侦听数量改变, 小于1, 直接强制覆盖1
export default {
  props: {
    goods: {
      type: Object,
      required: true
    }
  },
  watch: {
    goods: {
      deep: true, // 监听数据里某个属性的变化
      immediate: true, // 立即执行监听
      handler (newVal) {
        if (newVal.goods_count < 0) {
          this.goods.goods_count = 0
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
.my-counter {
  display: flex;
  .inp {
    width: 45px;
    text-align: center;
    margin: 0 10px;
  }
  .btn,
  .inp {
    transform: scale(0.9);
  }
}
</style>
