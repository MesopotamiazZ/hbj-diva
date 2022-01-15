<template>
  <view
    class='order-card'
    @click="showDetail"
  >
    <view class="order-name flex">
      <view class='order-name-text'>{{order_detail.order_name}}</view>
      <view
        class="order-name-tag"
        :class="{'active-status': order_detail.product.status === '正在进行'}"
      >{{order_detail.product.status}}</view>
    </view>
    <view class='order-content flex'>
      <view class='price'>
        <view class='price-text'>销售单号</view>
        <view class='price-value'>{{order_detail.order_id}}</view>
      </view>
      <view class='price'>
        <view class='price-text'>销售额</view>
        <view class='price-value'>{{order_detail.sale_price}}</view>
      </view>
      <view class='price'>
        <view class='price-text'>一级分销</view>
        <view class='price-value'>{{order_detail.level1_price}}</view>
      </view>
      <view class='price'>
        <view class='price-text'>二级分销</view>
        <view class='price-value'>{{order_detail.level2_price}}</view>
      </view>
      <!-- <view class='price'>
        <view class='price-text'>三级分销</view>
        <view class='price-value'>1，000</view>
      </view> -->
    </view>
    <template v-if="!showAll">
      <text class="iconfont icon-unfold" />
    </template>
    <template v-else>
      <text class="iconfont icon-fold" />
    </template>

    <view
      class='card-detail'
      v-if="showAll"
    >
      <view class='card-detail-item'>
        <view class='left'>活动日期</view>
        <view class='right'>{{order_detail.product.date}}</view>
      </view>
      <view class='card-detail-item'>
        <view class='left'>发布人</view>
        <view class='right'>{{order_detail.product.publisher}}</view>
      </view>
      <view class='card-detail-item'>
        <view class='left'>购买人</view>
        <view class='right'>{{order_detail.purchaser}}</view>
      </view>
      <view class='card-detail-item'>
        <view class='left'>一级推荐人</view>
        <view class='right'>{{order_detail.Recommender1}}</view>
      </view>
      <view class='card-detail-item'>
        <view class='left'>二级推荐人</view>
        <view class='right'>{{order_detail.Recommender2}}</view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      isCustomer: false,
      showAll: true,
      order_detail: {
        order_id: 1,
        order_name: 'xxxx美容活动',
        product: {
          "product_id": "337247259148161025",
          "product_name": "榴莲千层",
          "cover": "online/shz/cover_key/50eed15bcff63.png",
          "introduction": "活动时间发了卡时代峰峻脸上的肌肤及时的客服林静脸上的肌肤立刻收到就是的客服就是离开对方的索科洛夫家",
          "sale_price": "25.00",
          "level1_price": "5.00",
          "level2_price": "2.00",
          "level3_price": "1.00",
          "create_at": "1641366012",
          "update_at": "1641366012",
          "product_stock": "12",
          "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png",
          "status": '正在进行',
          "date": '2021-01-01至2021-12-31',
          "publisher": '1888888888'
        },
        status: '正在进行',
        sale_price: '1,000',
        level1_price: '500',
        level2_price: '200',
        level3_price: '100',
        purchaser: 'tigris',
        Recommender1: '张三',
        Recommender2: '李四',
      }
    }
  },
  onLoad() {

  },
  methods: {
    showDetail() {
      this.showAll = !this.showAll;
    }
  }
}
</script>

<style lang="scss" scoped>
.flex {
  display: flex;
}

.order-card {
  position: relative;
  box-sizing: border-box;
  width: 94%;
  margin: 0 auto;
  min-height: 220rpx;
  border-radius: 8rpx;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  margin-bottom: 20rpx;
  padding: 20rpx 50rpx 20rpx 20rpx;
}

.icon-unfold,
.icon-fold {
  position: absolute;
  right: 10rpx;
  top: 20rpx;
}

.order-name {
  width: 100%;

  .order-name-text {
    width: 80%;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
  }

  .order-name-tag {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid rgba(255, 51, 153, 0.2);
    color: rgb(255, 51, 153);
    background: rgba(255, 51, 153, 0.1);
    border-radius: 4rpx;
    flex: 1;
    font-size: 24rpx;
  }

  .active-status {
    border: 1px solid rgba(103, 194, 58, 0.2);
    color: rgb(103, 194, 58);
    background: rgba(103, 194, 58, 0.1);
  }
}

.order-content {
  justify-content: space-between;
  margin-top: 20rpx;

  .price {
    display: flex;
    flex-direction: column;

    .price-text {
      color: #999;
      margin-bottom: 10rpx;
    }

    .price-value {
      color: #000;
      font-weight: 600;
      text-align: center;
    }
  }
}

.card-detail {
  display: flex;
  flex-direction: column;
  margin-top: 10rpx;
  border-top: 1px solid #eee;
  .card-detail-item {
    display: flex;
    justify-content: space-between;
    padding: 10rpx 0;
    .left {
      color: #999;
    }

    .right {
      color: #000
    }
  }
}
</style>
