<template>
  <view class='profile-page'>
		<view class='customer-page' v-if="isCustomer">
			
		</view>
		<view class='business-page' v-if="!isCustomer">
			
		</view>
	</view>
</template>

<script>
  export default {
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

<style>
.index-page {
  width: 100vw;
  height: 100vh;
}
</style>
