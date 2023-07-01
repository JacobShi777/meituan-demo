<template>
	<view class="search-comp" @click="handleSearch">
		<view class="left">
			<image src="@/static/image/搜索.png" mode=""></image>
			<view class="content">
				天猫小店
			</view>
		</view>
		<view class="right">
			搜索
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchContent: ''
			};
		},
		methods: {
			handleSearch() {
				uni.navigateTo({
					url: '/pages/Search/Search'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
@import "@/uni_modules/uview-ui/index.scss";

.search-comp {
	margin-top: 20rpx;
	width: 100%;
	height: 60rpx;
	border: 1px solid orange;
	border-radius: 30rpx;
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	
	.left {
		height: 30rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		margin-left: 20rpx;
		
		image {
			height: 100%;
			width: 30rpx;
		}
		
		.content {
			margin-left: 20rpx;
			line-height: 30rpx;
			font-size: 20rpx;
		}
	}
	
	.right {
		height: 60rpx;
		width: 120rpx;
		line-height: 60rpx;
		background-color: orange;
		text-align: center;
		border-radius: 30rpx;
	}
	
}
</style>
