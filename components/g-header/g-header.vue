<template>
	<view class="g-header g-align-center g-justify-sb">
		<view>中国烟草 | 四川中烟工业有限责任公司</view>
		<view>
			<text class="user-box">{{userName}}</text>
			<text class="iconfont icon-close g-ml12" @click="handleCloseClick"></text>
		</view>
		<uni-popup ref="alertDialog" type="dialog">
			<uni-popup-dialog type="info" cancelText="取消" confirmText="退出" title="提示" content="是否退出系统？" @confirm="dialogConfirm"
			></uni-popup-dialog>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		name:"g-header",
		data() {
			return {
				userName: ''
			};
		},
		methods: {
			handleCloseClick() {
				this.$refs.alertDialog.open();
			},
			dialogConfirm() {
				// 清空登录信息
				uni.removeStorageSync('user_info');
				// 跳转至登录页面
				uni.redirectTo({
					url: '/pages/login/login',
				});
			}
		},
		created() {
			let userInfo = uni.getStorageSync('user_info');
			if(userInfo) {
				this.userName = userInfo.name;
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import '@/style/baseConfig.scss';
.g-header{
	height: 60rpx;
	width: 100%;
	padding: 0 40rpx 0 20rpx;
	background: $primary-backgroundColor;
	margin-bottom: 10rpx;
	color: #fff;
}
</style>