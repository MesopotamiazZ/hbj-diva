<!--  -->
<template>
  <view
    class="product-card"
    @longpress="popHandler"
    @click="onhandleClick"
  >
    <view class="product-card-main">
      <image
        class="main-avatar"
        :src="uploadHost + detail.cover"
        alt=""
      />
      <view class="main-content">
        <view class="product_name title-text">
          {{ detail.product_name }}
        </view>
        <view class="product_desc">
          {{ detail.introduction }}
        </view>
        <!-- <view class="product_tag">
          <view :class="[isUpCls, prodTagCls]">{{
          detail.status===1?'待上架':  detail.status === 2 ? "已上架" : "已下架"
          }}</view>
        </view> -->
      </view>
    </view>
    <view class="product-card-price card">
      <UniListItem>
        <view
          class="itle-text font-color-6"
          slot="header"
        > 售价 </view>
        <view
          slot="footer"
          class="font-color-3"
        >
          ¥{{
            detail.sale_price
          }}
        </view>
      </UniListItem>
      <UniListItem>
        <view
          class="itle-text font-color-6"
          slot="header"
        > 一级分销金额 </view>
        <view
          slot="footer"
          class="font-color-3"
        >
          ¥{{ detail.level1_price}}
        </view>
      </UniListItem>
      <UniListItem>
        <view
          class="itle-text font-color-6"
          slot="header"
        > 二级分销金额 </view>
        <view
          slot="footer"
          class="font-color-3"
        >
          ¥{{ detail.level2_price}}
        </view>
      </UniListItem>
    </view>
  </view>
</template>

<script>
import {
  mapMutations
} from "vuex";
import {
  UniListItem
} from '@dcloudio/uni-ui';

export default {
  props: {
    detail: Object,
  },
  //import引入的组件需要注入到对象中才能使用
  components: {
    UniListItem
  },

  data() {
    //这里存放数据
    return {
      prodTagCls: "prod-tag",
      prodTagSta1: "prod-tag-status1",
      prodTagSta2: "prod-tag-status2",
      uploadHost: "https://ryq-mall-ml.oss-cn-chengdu.aliyuncs.com/",
      operactor_btns: ["补货", "下架", "修改", "删除"],
      isShowOperactor: false,
      touchT: 0,
      touchE: 0,
    };
  },

  //监听属性 类似于data概念
  computed: {
    isUpCls() {
      return this.detail.status === 2 ? this.prodTagSta1 : "";
    },
    isHasStock() {
      return this.detail.product_stock && this.detail.product_stock !== "0" ?
        this.prodTagSta2 :
        "";
    },
  },
  //监控data中的数据变化
  watch: {},
  //方法集合
  methods: {
    ...mapMutations("product-manage-module", ["modifyProductList"]),
    onLongPress() {
      this.isShowOperactor = true;
    },
    onhandleClick() {
      this.nav("");
    },
    popHandler: async function () {
      uni.hideToast();
      console.log("detail", this.detail);
      await new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve(true);
        }, 100);
      });
      const that = this;
      uni.showActionSheet({
        itemList: that.detail.status === 2 ? // ? ["补货", "下架", "修改", "删除"]
          // : ["补货", "上架", "修改", "删除"],
          ["复制", "下架", "修改", "删除"] : ["复制", "上架", "修改", "删除"],
        success: function (res) {
          // if (res.tapIndex == 0) {
          //   that.add_stock();
          // } else
          console.log(res, "index");
          if (res.tapIndex == 0) {
            console.log("fuzhi");
            that.copy_prod(that.detail);
          } else {
            if (res.tapIndex == 1) {
              if (that.detail.status == 2) {
                that.down_prod();
              } else {
                that.put_prod();
              }
            } else if (res.tapIndex == 2) {
              that.edit_prod();
            } else if (res.tapIndex == 3) {
              that.del_prod();
            }
          }
        },
      });
    },
    //监控data中的数据变化
    // watch: {},
    //方法集合
    onLongPress() {
      this.isShowOperactor = true;
    },
    onhandleClick() {
      if (this.touchE - this.touchT < 350) {
        if (this.isShowOperactor) {
          this.isShowOperactor = false;
          return;
        }
        this.nav("product-manage/detail", {
          id: this.detail.product_id,
        });
      }
    },
    add_stock() {
      this.nav("product-manage/supplement", {
        id: this.detail.product_id,
      });
    },

    async put_prod() {

    },
    async del_prod() {

    },
    async down_prod() {

    },
    async copy_prod() {

    },
    edit_prod() {

    },
    nav: function (url, params = {}) {
      navLinkToManage(url, params);
    },
    touchEnd() {
      this.touchE = new Date().getTime();
    },
    nav: function (url, params = {}) {
      navLinkToManage(url, params);
    },
  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {},
};
</script>

<style lang="scss">
//@import url(); 引入公共css类
.product-card {
  position: relative;

  .product-card-main {
    min-height: 230rpx;
    display: flex;
    padding: 40rpx 20rpx;
    box-sizing: border-box;

    .main-avatar {
      width: 160rpx;
      height: 160rpx;
      margin-right: 20rpx;
      border-radius: 20rpx;
    }

    .main-content {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    // .product-card-mian {}
    .product_desc {
      font-size: 28rpx;
      font-family: PingFangSC-Regular, PingFang SC;
      font-weight: 400;
      color: #999999;
      text-overflow: -o-ellipsis-lastline;
      overflow: hidden;
      text-overflow: ellipsis;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
    }
  }

  .product-card-price {}

  /deep/ .uni-list-item {
    height: 108rpx;
    border-top: 1px solid #eaeaea;
  }

  .title-text {
    font-size: 34rpx;
    font-family: PingFangSC-Regular, PingFang SC;
    font-weight: 400;
    color: #333333;
  }

  .prod-tag {
    display: inline-block;
    // min-width: 120rpx;
    height: 48rpx;
    line-height: 48rpx;
    padding: 0 16rpx;
    background: rgba(102, 102, 102, 0.12);
    border-radius: 30rpx;
    font-size: 30rpx;
    font-family: PingFangSC-Regular, PingFang SC;
    font-weight: 400;
    color: #666666;
    text-align: center;
  }

  .prod-tag+.prod-tag {
    margin-left: 20rpx;
  }

  .prod-tag-status1 {
    background: rgba(70, 203, 129, 0.12);
  }

  .prod-tag-status2 {
    background: rgba(3, 122, 238, 0.12);
  }
}

.operactor-wrap {
  position: absolute;
  height: 80rpx;
  // line-height: 80rpx;
  display: flex;
  flex-wrap: nowrap;
  top: 80rpx;
  right: 20rpx;
  border-radius: 20rpx;
  background-color: #037aee;
  color: #fff;

  .operactor-wrap-item {
    position: relative;
    text-align: center;
    width: 100rpx;
    padding: 20rpx;
    box-sizing: border-box;
  }

  .operactor-wrap-item+.operactor-wrap-item:before {
    position: absolute;
    content: "";
    top: 26rpx;
    left: 0rpx;
    width: 1rpx;
    height: 30rpx;
    background-color: #eaeaea;
  }
}
</style>
