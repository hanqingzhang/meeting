<template>
	<view class="g-menu">
		<view class="menu-item g-flex-center g-flex-box-column" v-for="menu in menuList" :key="menu.id" @click="handleMenuClick(menu)" :class="[{'active': menu.pathUrl === activeMenu}]">
			<text class="iconfont" :class="[menu.icon]"></text>
			<text class="title">{{menu.title}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"g-menu",
		data() {
			return {
				menuList: [
					{id: 1,title: '当前会议', pathUrl: '/pages/current-meeting/current-meeting', icon: 'icon-hangzhengguanli-huiyishiguanli'},
					{id: 2,title: '历史会议', pathUrl: '/pages/history-meeting/history-meeting', icon: 'icon-lishidingdan'},
					{id: 3,title: '创建会议', pathUrl: '/pages/create-meeting/create-meeting', icon: 'icon-meeting-management-my-meeting'},
					{id: 4,title: '修改议题', pathUrl: '/pages/update-issues/update-issues', icon: 'icon-hetongtiaokuanxiugaishenqing-02'},
					{id: 5,title: '发起投票', pathUrl: '/pages/launch-vote/launch-vote', icon: 'icon-menu_zxtp'},
					{id: 6,title: '回到同屏', pathUrl: '/pages/back-screen/back-screen', icon: 'icon-fuzhi'},
				],
				activeMenu: ''
			};
		},
		methods: {
			handleMenuClick(menu) {
				uni.redirectTo({
					url: menu.pathUrl
				});
			}
		},
		created() {
			let pages = getCurrentPages();
			if(pages.length < 1){
				return null
			}else{
				let index = pages.length - 1;
				let current = pages[index];
				this.activeMenu = '/' + current.route;
			}
		},
	}
</script>

<style lang="scss">
	@import '@/style/baseConfig.scss';
.g-menu{
	height: 100%;
	width: 80rpx;
	background: #fff;
	padding: 10rpx 0 10rpx 7rpx;
	.menu-item{
		padding: 7rpx 7rpx 7rpx 0;
		color: #333;
		border-radius: 5rpx 0 0 5rpx;
		&.active{
			color: #fff;
			background: $primary-background-color;
		}
		.iconfont{
			line-height: 35rpx;
			font-size: 35rpx;
		}
		.title{
			font-size: 13rpx;
		}
	}
}
</style>