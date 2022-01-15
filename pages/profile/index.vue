<template>
  <view class='profile-page'>
    <view class="userinfo flex">
      <view class="image-wrap">
        <image
          class="img"
          alt="图片"
          :src="userinfo.avatar || defaultAvatar"
        />
        <!--

@longpress="popModal"
          @touchstart="touchStart"
          @touchend="touchEnd"

 -->
      </view>

      <view class="fb info">
        <view class="left fd">
          <view class="nickname fb">
            {{userInfo.nickname || "请登入"}}
						<text class="iconfont icon-right"></text>
          </view>
          <template v-if="userInfo.nickname">
            <view class="mobile fb">
              <text class="">
                {{userInfo.mobile
              ? "手机号：" +
              hideMobileStr
              : userInfo.nickname &&
              "获取手机号"}}
              </text>
							<text class="iconfont icon-right"></text>
            </view>
          </template>
        </view>
      </view>
    </view>

		<view class='operactor-btns flex'>
			<view class="order-btn" v-if="!isCustomer" @click="checkOrder">查看订单</view>
			<view class="quit-btn">退出登陆</view>
		</view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      userInfo: {},
      isCustomer: false,
      defaultAvatar: require('@/static/default-avatar.png')
    }
  },
  onLoad() {

  },
  computed: {
    hideMobileStr() {
      if (this.userInfo.mobile) return this.userInfo.mobile.replace(/^(\d{3})\d{4}(\d{4})$/, "$1****$2")
      else return ''
    }
  },
  methods: {
		checkOrder() {
			uni.navigateTo({
        url: '/pages/order/index'
      });
		}
  }
}
</script>

<style lang="scss" scoped>
.index-page {
  width: 100vw;
  height: 100vh;
}

.flex {
  display: flex;
}

.fb {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.fd {
    display: flex;
    // align-items: center;
    justify-content: center;
    flex-direction: column;
}

.userinfo {
  // background: transparent;
  // box-sizing: border-box;
	height: 240rpx;
  padding: 0 40rpx;
  // height: 120px;
  color: #fff;
  border-radius: 0 0 80rpx 80rpx;
  padding-bottom: 40rpx;

  .avatar-wrap {
    width: 140rpx;
    height: 140rpx;
  }

  .info {
		flex: 1;
    text-align: left;
    height: 100%;
    width: calc(100% - 140rpx);
    box-sizing: border-box;
    padding-left: 20rpx;

    .left {
      width: 100%;
      height: 100%;
      justify-content: space-around;
    }

    .nickname {
      font-size: 36rpx;
			color: #000;
    }

    .mobile {
      width: 100%;
      font-size: 28rpx;

      .iconfont {
        font-size: 36rpx;
      }
    }
  }
}

.image-wrap {
  margin: 0 auto;
  width: 140rpx;
  height: 140rpx;
  border-radius: 50%;
  margin-bottom: 60rpx;
  margin-top: 40rpx;
  position: relative;
  overflow: hidden;
  background: #efefef;

  .img {
    width: 140rpx;
    height: 140rpx;
  }

  .modal-mask-img {
    background: rgba(0, 0, 0, 0.5);
    position: absolute;
    width: 400rpx;
    height: 400rpx;
    top: 0;
    z-index: 9;
  }

  .update-img-btn {
    width: 400rpx;
    height: 100rpx;
    position: absolute;
    z-index: 99;
    background: #037aee;
    color: #fff;
    bottom: 0;
    animation: ans 400ms;
  }
}

.operactor-btns {
	position: fixed;
	bottom: 40rpx;
	width: 100%;

	view {
		display: flex;
		justify-content: center;
		align-items: center;
		flex: 1;
		margin: 0 40rpx;
		height: 80rpx;
		line-height: 80rpx;
		border-radius: 80rpx;
	}

	view.order-btn {
		border: 1px solid #555;
		background: #eee;
		color: #000;
	}
	view.quit-btn {
		border: 1px solid #037aee;
		background: #037aee;
		color: #fff;
	}
}
</style>
