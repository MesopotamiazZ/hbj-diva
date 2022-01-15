<!--  -->
<template>
  <view class='product-list'>
    <UniList>
      <view
        class="card"
        v-for="item in productList"
        :key="item.product_id"
      >
        <ProductCard
          :detail="item"
          ref="cardRef"
        />
      </view>
    </UniList>
  </view>
</template>

<script>
import ProductCard from '@/components/product-card';
import {
  uniList
} from '@dcloudio/uni-ui';

export default {
  //import引入的组件需要注入到对象中才能使用
  components: {
    ProductCard,
    uniList,
  },
  data() {
    //这里存放数据
    return {
      productList: [{
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
        "status": 1,
      },{
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
        "status": 1,
      },{
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
        "status": 1,
      },{
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
        "status": 1,
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      },{
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
        "cover_url": "https://resource-malicake-mall.fosuss.com/online/shz/cover_key/50eed15bcff63.png"
      } ]
    };
  },
  //监听属性 类似于data概念
  computed: {},
  //监控data中的数据变化
  watch: {},
  //方法集合
  methods: {

  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {

  },
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {

  },
}
</script>

<style lang="scss">
.product-list {
  padding-bottom: 100rpx;
}

/deep/ .uni-list {
  box-sizing: border-box;
  padding: 0 20rpx;
  background-color: transparent !important;
}

.card {
  width: 100%;
  background-color: #fff;
  box-sizing: border-box;
  padding: 0 20rpx;
  border-radius: 20rpx;
  overflow: hidden;
  border: none;
  margin-bottom: 20rpx;
}

.card-title {
  height: 96rpx;
  display: flex;
  align-items: center;
  font-size: 40rpx;
  font-weight: bold;
  border-bottom: 1rpx solid #EAEAEA;
}
</style>
