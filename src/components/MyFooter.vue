<template>
  <!-- 底部 -->
  <div class="my-footer">
    <!-- 全选 -->
    <div class="custom-control custom-checkbox">
      <input type="checkbox" class="custom-control-input" id="footerCheck" 
      v-model="isAll"
      />
      <label class="custom-control-label" for="footerCheck">全选</label>
    </div>
    <!-- 合计 -->
    <div>
      <span>合计:</span>
      <span class="price">¥ {{allPrice}}</span>
    </div>
    <!-- 按钮 -->
    <button type="button" class="footer-btn btn btn-primary">结算 ( {{allCount}} )</button>
  </div>
</template>

<script>
// 1. 传递goodsList--->Myfooter
// 2. 全选框v-model->isAll
// 3. isAll的get和set方法
export default {
  props: {
    goodList: {
      type: Array,
      required: true
    }
  },
  computed: {
    isAll: {
      get () {
        return this.goodList.every((item) => item.goods_state)
      },
      set (newVal) {
        this.goodList.forEach((item) => (item.goods_state = newVal))
      }
    },
    // 总件数
    allCount () {
      return this.goodList.reduce((pre, curr) => {
        if (curr.goods_state) {
          return pre + curr.goods_count
        } else {
          return pre
        }
      }, 0)
    },
    allPrice () {
      return this.goodList.reduce((pre, curr) => {
        if (curr.goods_state) {
          return pre + curr.goods_price * curr.goods_count
        } else {
          return pre
        }
      }, 0)
    }
  }
}
</script>

<style lang="less" scoped>
.my-footer {
  position: fixed;
  z-index: 2;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
  background: #fff;

  .price {
    color: red;
    font-weight: bold;
    font-size: 15px;
  }
  .footer-btn {
    min-width: 80px;
    height: 30px;
    line-height: 30px;
    border-radius: 25px;
    padding: 0;
  }
}
</style>
