<template>
	<view class="login-wrapper">
		<view class="login-box">
			<view class="login-title g-mb24">无纸化会议系统</view>
			<uni-forms :modelValue="formData"  ref="form" :rules="rules">
				<uni-forms-item name="name">
					<uni-easyinput prefixIcon="person" type="text" v-model="formData.name" placeholder="请输入用户名" />
				</uni-forms-item>
				<uni-forms-item name="password">
					<uni-easyinput prefixIcon="locked" type="password" v-model="formData.password" placeholder="请输入密码" />
				</uni-forms-item>
			</uni-forms>
			<button class="submit-btn g-mt12" @click="submitForm" >登 录</button>
		</view>
		<view class="login-logo">中国烟草 | 四川中烟工业责任有限公司</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				formData: {
					name: '',
					password: '',
				},
				rules: {
					name: {
						rules: [{required: true, errorMessage: '请输入用户名'}]
					},
					password: {
						rules: [{required: true, errorMessage: '请输入密码'}]
					},
				}
			};
		},
		methods: {
			// 登录
			submitForm() {
				this.$refs.form.validate().then(res=>{
					console.log('表单数据信息：', res);
					uni.setStorageSync('user_info', {name: '张大伟', token: 'sdhfshueriwjwqe6723h42u34jrwu329'});
					// 跳转至第一个页面
					uni.redirectTo({
						url: '/pages/create-meeting/create-meeting',
					});
				}).catch(err =>{
					console.log('表单错误信息：', err);
				})
			}
		},
		onLoad() {
			// TODO 判断是否已经登录
			if(uni.getStorageSync('user_info')) {// 如果已经登录
				uni.redirectTo({
					url: '/pages/create-meeting/create-meeting',
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import '@/style/baseConfig.scss';
.login-wrapper{
	height: 100%;
	width: 100%;
	// background: #fdeae9;
	background-image:url('../../static/login/back.png');
	background-size: 100% 100%;
	position: relative;
	.login-box{
		width: 221rpx;
		height: 250rpx;
		background-image:url('../../static/login/login.png');
		background-size: 100% 100%;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		border-radius: 8rpx;
		.login-title{
			font-size: 28rpx;
			text-align: center;
		}
		.submit-btn{
			color: #fff;
			background: $primary-backgroundColor;
		}
	}
	.login-logo{
		position: absolute;
		left: 20rpx;
		top: 20rpx;
	}
}
</style>
