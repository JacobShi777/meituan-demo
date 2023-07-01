<template>
	<view class="homepage-page" :style="{
		paddingTop: navBarHeight,
	}">
		<NavBar></NavBar>
		<view class="content">			
			<Search></Search>
			<NavItems></NavItems>
			<NoticeBar></NoticeBar>
			<BoxItems ref="boxItems"></BoxItems>
		</view>
	</view>
</template>

<script>
	import NavBar from './components/NavBar.vue'
	import Search from './components/Search.vue'
	import NavItems from './components/NavItems.vue'
	import NoticeBar from './components/NoticeBar.vue'
	import BoxItems from './components/BoxItems.vue'
	export default {
		components: {
			NavBar,
			Search,
			NavItems,
			NoticeBar,
			BoxItems,
		},
		data() {
			return {
				navBarHeight: undefined
			}
		},
		onLoad() {
			this.navBarHeight = 44 + uni.getSystemInfoSync().statusBarHeight + "px";
		},
		onReachBottom() {
			this.$refs.boxItems.getData()
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
.homepage-page {
	background-color: #F6F6F6;
	.content {
		padding: 20rpx;
	}
}
</style>
