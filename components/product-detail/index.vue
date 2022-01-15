<!--  -->
<template>
  <view class="product-detail content">
    <uni-swiper-dot
      :info="[productDetail.cover]"
      :current="current"
      mode="round"
      :dotsStyles="dotsStyles"
    >
      <swiper
        class="swiper-box"
        interval="{5000}"
        :circular="true"
        @change="onSwiperChange"
      >
        <swiper-item
          v-for="(item, index) in [productDetail.cover]"
          :key="index"
        >
          <!-- <view class="swiper-item"> -->
          <image
            class="swiper-img"
            :src="uploadHost + item"
            mode="widthFix"
            alt=""
          />
          <!-- </view> -->
        </swiper-item>
      </swiper>
    </uni-swiper-dot>

    <view class="p-info">
      <view class="p-name fb">
        <view class="name">
          {{ productDetail.product_name }}
        </view>
      </view>

      <!-- <view
   class="flex"
   style="margintop: 10rpx"
 >
        <view class="desc flex">
          <view
            class="desc-item fc"
            v-for="item in productDetail.product_tags"
            :key="item.name"
            >{{ item.name }}</view
          >
        </view>
      </view> -->

      <view class="price-box fb">
        <view class="price flex">
          <sub>¥</sub>{{ productDetail.sale_price }}
        </view>
      </view>
    </view>

    <view class="p-desc">
      <view class="title">
        <view class="v-line" />
        <text class="text">商品信息</text>
        <view class="v-line" />
      </view>
      <view
        class="detail_wrap"
        style="width: 100%"
      >
        {{ productDetail.introduction }}
      </view>
    </view>

    <button class="buy-btn">购买</button>
  </view>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
import {
  mapState,
  mapActions,
  mapMutations
} from "vuex";

export default {
  //import引入的组件需要注入到对象中才能使用
  components: {},
  data() {
    //这里存放数据
    return {
      extension: false,
      productDetail: {
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
      },
      productId: "",
      uploadHost: "https://ryq-mall-ml.oss-cn-chengdu.aliyuncs.com/",
      current: 0,
      dotsStyles: {
        backgroundColor: "#fff",
        selectedBackgroundColor: "#FE7945",
        border: "#fff",
        selectedBorder: "#FE7945",
        width: 12,
      },
    };
  },
  //监听属性 类似于data概念
  computed: {
    // ...mapState("product-manage-module", ["productDetail"]),
    // nodes() {
    //   return this.productDetail?.product_detail?.description?.replace(
    //     /\<img/gi,
    //     "<img style=width:100%;height:auto"
    //   );
    // },
    // desc_imgs() {
    //     return this.parseImgTagStr(this.productDetail.product_detail.description);
    // }
  },
  //监控data中的数据变化
  watch: {},
  //方法集合
  onShow() {
    this.init();
  },
  methods: {
    onSwiperChange(e) {
      console.log(e);
      this.current = e.detail.current;
    },
    openExtension() {
      this.extension = !this.extension;
    },
    parseImgTagStr(str) {
      function getimgsrc(htmlstr) {
        let tem;
        var reg = /<img.+?src=('|")?([^'"]+)('|")?(?:\s+|>)/gim;
        var arr = [];
        while ((tem = reg.exec(htmlstr))) {
          arr.push(tem[2]);
        }
        return arr;
      }
      const arr = getimgsrc(str).map((item) => item.split(".com/")[1]);
      console.log("arr", arr);
      return arr;
    },
    async init() {
      // const {
      //     options
      // } = getCurrentPages()[0];
      const res = await this.getProductDeatilAction({
        product_id: this.productId,
      });
      this.extension = false;
    },
    nav: function (url, params = {}) {

    },
    add_stock() {
      this.nav("product-manage/supplement", {
        id: this.productId,
      });
    },
    async put_prod() {

    },
    async del_prod() {

    },
    async down_prod() {

    },
    edit_prod_info() {
      uni.removeStorageSync("add-sku");
      uni.removeStorageSync("cover_key");
      uni.removeStorageSync("html");
      uni.removeStorageSync("product_image_key");
      uni.removeStorageSync("product_detail_image_key");
      uni.removeStorageSync("specs-data");
      this.nav("product-manage/edit", {
        id: this.productId,
      });
    },
    edit_prod() {
      uni.removeStorageSync("specs-data");
      uni.setStorageSync("specs-data", this.productDetail.product_specs);
      uni.setStorageSync('add-sku', this.productDetail.product_skus.map((item) => ({
        ...item,
        title: item.specs.map((spec) => (spec.spec_value.value)).join(','),
        stock: item.stock.current
      })))
      this.nav("product-manage/sku/sku-info", {
        id: this.productId,
      });
    },
  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  onLoad(options) {
    this.productId = options.id;
  },
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {
    this.init();
  },
};
</script>

<style lang="scss" scoped>
//@import url(); 引入公共css类
.product-detail {
  padding: 0 !important;

  .swiper-box {
    height: 520rpx;
  }

  .swiper-img {
    width: 100%;
    // height: 5;
  }

  // /deep/ .uni-swiper__dots-item {
  //     height: 10rpx!important;
  //     border-radius: 5rpx!important;
  //     background-color: #fff!important;
  //     // width: 15rpx!important;
  // }
  .p-info {
    // margin-top: 24rpx;
    padding: 20rpx;
    box-sizing: border-box;
    margin-bottom: 20rpx;
    background-color: #fff;

    .iconfont {
      color: #333;
    }

    .p-name {
      font-size: 36rpx;
      color: #333;
      font-weight: bold;
      margin-bottom: 10rpx;

      .name {
        font-size: 36rpx;
        // max-width: 80%;
        // line-height: 40px;
        word-break: break-all;
      }

      .iconfont {
        height: 60rpx;
        font-size: 60rpx;
        line-height: 60rpx;
      }

      .share {
        padding: 0;
        margin: 0;
        background-color: #fff;
        width: 100rpx;
        // height: 80px;
        line-height: 24rpx;
        font-size: 24rpx;
      }
    }

    .price-box {
      position: relative;
      width: 100%;
      margin: 10rpx 0;
      font-size: 36rpx;

      .price {
        font-weight: bold;
        // font-family: PingFangSC-Semibold, PingFang SC;
        font-weight: 600;
        color: #fe2811;
      }

      sub {
        position: relative;
        display: inline-block;
        font-size: 24rpx;
        // top: -10rpx;
      }

      .old {
        font-size: 30rpx;
        margin-left: 20rpx;
        text-decoration: line-through;
        color: #666;
      }

      .pack {
        position: absolute;
        right: 0;
        font-size: 24rpx;
        font-family: PingFangSC-Regular, PingFang SC;
        font-weight: 400;
        color: #999999;
      }
    }

    .member-price-tag {
      display: flex;
      width: 180rpx;
      height: 34rpx;
      border-radius: 17rpx;
      border: 1rpx solid #333333;
      overflow: hidden;
      margin-bottom: 20rpx;

      .left {
        // display: inline-block;
        width: 60rpx;
        background-color: #333;
        color: #ffdbb0;
        font-size: 22rpx;
        font-family: PingFangSC-Regular, PingFang SC;
        font-weight: 400;
        text-align: center;
      }

      .right {
        // display: inline-block;
        flex: 1;
        color: #333;
        font-size: 22rpx;
        font-family: PingFangSC-Regular, PingFang SC;
        font-weight: 400;
        text-align: center;
      }
    }

    .other {
      padding-bottom: 16rpx;

      .sale {
        font-size: 26rpx;
        color: #999;
      }
    }

    .desc-item {
      // 补贴0.31
      border-radius: 4rpx;
      background: rgba(153, 153, 153, 0.2);
      // border: 2px solid #00D0BF;
      // height: 36px;
      padding: 2rpx 12rpx;
      margin-right: 10rpx;
      font-size: 24rpx;
      color: #999999;
    }

    .tags {
      border: 2rpx solid #00d0bf;
      color: #00d0bf;
      background: #fff;
    }

    ._money {
      font-size: 24rpx;
    }
  }

  .p-desc {
    .title {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 28rpx;
      height: 100rpx;
      margin-bottom: 0;
      background-color: #fff;

      .text {
        margin: 0 20rpx;
      }

      .v-line {
        width: 4rpx;
        height: 20rpx;
        background: linear-gradient(90deg, #f96822 0%, #ffa77e 100%);
        border-radius: 2rpx;
      }
    }
  }

  .detail_wrap {
    box-sizing: border-box;
    padding: 20rpx;
    background: #fff;
    padding-bottom: 120rpx;
  }

  .buy-btn {
    position: fixed;
    bottom: 20rpx;
    left: 4%;
    width: 92%;
    height: 80rpx;
    background: #047cec;
    border-color: #047cec;
    border-radius: 40rpx;
    color: #fff;
  }

  #editor {
    height: fit-content;
  }
}
</style>
