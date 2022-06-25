<template>
	<view class="update-issues page-common">
		<g-header></g-header>
		<view class="page-main">
			<g-menu></g-menu>
			<view class="page-content">
				<basic-content></basic-content>
			</view>
		</view>
	</view>
</template>

<script>
	import gHeader from "@/components/g-header/g-header.vue";
	import gMenu from "@/components/g-menu/g-menu.vue";
	import basicContent from "./content.vue";
	export default {
		name: 'update-issues',
		components:{
			gHeader,
			gMenu,
			basicContent
		},
		data() {
			return {};
		}
	}
</script>

<style lang="scss" scoped>
	@import '@/style/page-common.scss';
</style>
