<template>
  <view class='order-page'>
    <view class='content'>
      <OrderCard />
      <OrderCard />
    </view>
  </view>
</template>

<script>
import {
  UniList
} from '@dcloudio/uni-ui';
import OrderCard from '@/components/order-card';

export default {
  components: {
    OrderCard,
  },
  data() {
    return {
      isCustomer: false,
    }
  },
  onLoad() {

  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
.order-page {
  width: 100vw;
  height: 100vh;

  .content {
    min-height: 100%;
    background: #f9f9f9;
    box-sizing: content-box;
  }
}
</style>
