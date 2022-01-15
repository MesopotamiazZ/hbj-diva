<template>
  <view class='index-page'>
    <view
      class='customer-page'
      v-if="isCustomer"
    >
			<ProductDetail />
    </view>
    <view
      class='business-page'
      v-if="!isCustomer"
    >
      <ProductList />
      <view
        class='add-product'
        @click="addProduct"
      >
        <image
          :src="addIcon"
          mode="widthFix"
        />
      </view>
    </view>
  </view>
</template>

<script>
import ProductList from '@/components/product-list';
import ProductDetail from '@/components/product-detail';

export default {
  components: {
    ProductList,
		ProductDetail,
  },
  data() {
    return {
      isCustomer: false,
      addIcon: require('@/static/add-bold.png')
    }
  },
  onLoad() {

  },
  methods: {
    addProduct() {
      uni.navigateTo({
        url: '/pages/add/index'
      });
    }
  }
}
</script>

<style lang="scss">
.index-page {
  height: 100vh;
  width: 100vw;
  
	.customer-page {
		background: #f9f9f9;
	}
	.business-page {
		background: #f9f9f9;
	}
}

/deep/ .uni-list {
  box-sizing: border-box;
  padding: 0 20rpx;
  background-color: transparent !important;
}

.add-product {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  bottom: 20rpx;
  right: 20rpx;
  width: 120rpx;
  height: 120rpx;
  border-radius: 50%;
  background: #047cec;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.add-product image {
  width: 50%;
}
</style>
