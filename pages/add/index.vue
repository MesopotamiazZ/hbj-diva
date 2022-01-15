<template>
  <view class='add-product-page'>
    <view class="wrap">
      <view class="title flex">商品信息</view>
      <view class="card">
        <UniListItem style="borderbottom: 1px solid #eaeaea">
          <view
            slot="header"
            class="slot-box flex left"
          >商品名称</view>
          <template slot="footer">
            <input :placeholder-style="defaultTipStyle" v-model="params.product.product_name" class="ease-input" type="text" placeholder="请输入" />
            <!-- <text class="iconfont icon-right" /> -->
          </template>
        </UniListItem>
        <!-- 商品封面图 -->
        <view
          class="fd"
          style="padding-bottom: 40rpx"
          @click="
            _nav('make-order/uploadImg', {
              key: cover_key,
              length: 1,
              auto: 1,
            })
          "
        >
          <UniListItem>
            <view
              slot="header"
              class="slot-box flex left"
            >封面图上传</view>
            <template slot="footer">
              <view class="flex">
                {{ params.product.cover ? "1 / 1" : "0 / 1" }}</view>
            </template>
          </UniListItem>
          <view class="img-list flex">
            <!-- {{ params.cover}} -->
            <view
              class="fc img-wrap"
              v-if="params.product.cover"
            >
              <image
                class="img"
                mode="widthFix"
                :key="params.product.cover"
                :src="params.product.cover"
              />
            </view>
            <view
              v-if="!params.product.cover"
              :class="
                params.product.cover == ''
                  ? 'up_img_wrap empty-box'
                  : 'up_img_wrap'
              "
            >
              <button class="btn fc">
                <text class="iconfont iconxinzeng"></text>
              </button>
            </view>
          </view>
        </view>
      </view>

      <view class="title flex">
        商品价格及分销
      </view>
      <view class="card">
        <UniListItem>
          <view
            slot="header"
            class="slot-box flex left1"
          >售价</view>
          <!-- <view slot="footer"> ¥{{params.product.market_price}} </view> -->
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.product.sale_price" class="ease-input" type="number" placeholder="请输入" />
            <!-- <text class="iconfont icon-right" /> -->
          </template>
        </UniListItem>
        <UniListItem>
          <view
            slot="header"
            class="slot-box flex left1"
          >一级分销金额</view>
          <!-- <view slot="footer"> {{params.product.member_price == 0 ? "-" : params.product.member_price}} </view> -->
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.product.level1_price" class="ease-input" type="number" placeholder="请输入" />
          </template>
        </UniListItem>
        <UniListItem>
          <view
            slot="header"
            class="slot-box flex left1"
          >二级分销金额</view>
          <!-- <view slot="footer"> {{params.product.member_price == 0 ? "-" : params.product.member_price}} </view> -->
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.product.level2_price" class="ease-input" type="number" placeholder="请输入" />
          </template>
        </UniListItem>
        <UniListItem>
          <view
            slot="header"
            class="slot-box flex left1"
          >三级分销金额</view>
          <!-- <view slot="footer"> {{params.product.member_price == 0 ? "-" : params.product.member_price}} </view> -->
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.product.level3_price" class="ease-input" type="number" placeholder="请输入" />
          </template>
        </UniListItem>
      </view>

      <view class="title flex">商品详情</view>
      <view class="card">
        <UniListItem style="borderbottom: 1px solid #eaeaea">
          <view
            slot="header"
            class="slot-box flex left1"
          >商品简介</view>
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.product.introduction" class="ease-input" type="text" placeholder="请输入" />
            <!-- <text class="iconfont icon-right" /> -->
          </template>
        </UniListItem>

        <UniListItem style="bordertop: 1px solid #eaeaea">
          <view
            slot="header"
            class="flex"
          >商品详情图片</view>
          <template slot="footer">
            <view class="flex">
              {{ params.product.product_detail_images.length + " / 6" }}</view>
          </template>
        </UniListItem>
        <view class="img-list flex">
          <view
            v-for="src in params.product.product_detail_images"
            :key="src"
            class="fc img-wrap"
          >
            <image
              class="img"
              mode="widthFix"
              :key="src"
              :src="src"
            />
          </view>
          <view
            v-if="params.product.product_detail_images.length < 6"
            :class="
                params.product.product_detail_images.length == 0
                  ? 'up_img_wrap empty-box'
                  : 'up_img_wrap'
              "
          >
            <button class="btn fc">
              <text class="iconfont iconxinzeng"></text>
            </button>
          </view>
        </view>
      </view>

      <view class="title flex">
        发布人认证
      </view>
      <view class="card">
        <UniListItem style="borderbottom: 1px solid #eaeaea">
          <view
            slot="header"
            class="slot-box flex left1"
          >手机号</view>
          <template slot="footer">
            <input placeholder-style="color:#999" v-model="params.publisher.mobile" class="ease-input" type="text" placeholder="请输入" />
            <!-- <text class="iconfont icon-right" /> -->
          </template>
        </UniListItem>
      </view>

      <view class="operactor-btns btns">
        <button class="submit-btn" type="primary" @click="putProd">
          立即上架
        </button>
      </view>
    </view>
  </view>
</template>

<script>
import {
  uniList,
  UniListItem
} from "@dcloudio/uni-ui";

export default {
  components: {
    uniList,
    UniListItem,
  },
  data() {
    return {
      isCustomer: false,
      defaultTipStyle: "font-size: 34rpx!important;font-family: PingFangSC-Regular, PingFang SC;font-weight: 400;color: #999999;",
      params: {
        product: {
          product_name: '',
          cover: '',
          sale_price: '',
          level1_price: '',
          level2_price: '',
          level3_price: '',
          introduction: '',
          product_detail_images: ''
        },
        publisher: {
          mobile: ''
        }
      },
    }
  },
  onLoad() {

  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
.add-product-page {
  width: 100vw;
  height: 100vh;
}

.left:before {
  content: "*";
  height: 20rpx;
  display: inline-block;
  line-height: 100%;
  font-size: 36rpx;
  color: red;
}

.wrap {
  padding: 0 20rpx;
  box-sizing: border-box;
  background: #f9f9f9;
}

.card {
  box-sizing: border-box;
  margin-top: 20rpx;
  width: 100%;
  background-color: #fff;
  box-sizing: border-box;
  padding: 0 10px;
  border-radius: 10px;
  overflow: hidden;
  border: none;
}

.img-list {
  width: 100%;
  align-items: flex-start;
  flex-shrink: 0;
  flex-wrap: wrap;

  .img-wrap {
    margin: 10rpx;
    overflow: hidden;
    width: 200rpx;
    height: 200rpx;
    border-radius: 8rpx;
  }

  .img {
    width: 100%;
    // height: calc(33.33vw - 14px);
    background: #d8d8d8;
    border-radius: 8rpx;
  }
}

.up_img_wrap {
  margin: 10rpx;
  width: 200rpx;
  height: 200rpx;
  border-radius: 8rpx;
  background: #fff;
  border: 2rpx dashed #cecece;

  .btn {
    background-color: #fff;
    width: 100%;
    height: 100%;

    .iconfont {
      color: #cecece;
      font-size: 100rpx;
    }
  }
}

.title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;
  font-size: 20px;
  font-weight: bold;
  padding-top: 10px;
  margin-bottom: 5px;

  &>.title-right {
    font-size: 34rpx;
    font-family: PingFangSC-Regular, PingFang SC;
    font-weight: 400;
    color: #999999;

    .title-right-switch {
      margin-left: 20rpx;
    }
  }
}

.card .btns {
  padding: 0;

  .btn {
    font-size: 34rpx;
    font-family: PingFangSC-Regular, PingFang SC;
    font-weight: 400;
    color: #ffffff;
  }
}

.operactor-btns {
  padding: 40rpx 0 20rpx 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.btns .btn {
  height: 80rpx;
}

.submit-btn {
  width: 92%;
  height: 80rpx;
  line-height: 80rpx;
  background: #047cec;
  border-color: #047cec;
  border-radius: 40rpx;
  color: #fff;
  margin-bottom: 40rpx;
}

/deep/ .uni-input-placeholder {
  text-align: right;
  font-size: 28rpx;
}

/deep/ .uni-input-input {
  text-align: right;
  font-size: 28rpx !important;
}

/deep/ .uni-list-item {
  height: 108rpx !important;
}

/deep/ .uni-input-input {
  font-size: 34rpx;
}

/deep/ .uni-list--border:after {
  background: #fff;
}

.default-tip-style {
  font-size: 34rpx;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: #999999;
}

.flex {
  display: flex;
}

.fc {
  display: flex;
  justify-content: center;
  align-items: center;
}

.slot-box {
  color: #666 !important;
}

.ease-input {
  text-align: right;
  width: 50vw;
  height: 100%;
}
</style>
