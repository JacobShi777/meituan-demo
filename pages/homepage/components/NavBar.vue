<template>
	<view>
		<MysNavBar
		  :mysNavConfig="mysNavConfig"
		>
			<template #left>
				<view class="left-slot" @click="handleClick">
					<image class="nv_icon" src="/static/MysNavBar/map.png" />
					<view class="text">
						丽园南路学校
					</view>
					<image class="back_r" src="/static/MysNavBar/back_r.png" />
				</view>
			</template>
		</MysNavBar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mysNavConfig: {
					navFixed: true,
					bgColor: '#FFDC42',
					isHome: true,
					hideDefaultLeft: true,
				}
			};
		},
		methods: {
			handleClick() {
				uni.navigateTo({
					url: "/pages/address/address"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
@import "@/uni_modules/uview-ui/index.scss";

.nv_icon {
  width: 36rpx;
  height: 36rpx;
}

.back_r {
	width: 20rpx;
	height: 20rpx;
	margin-left: 7rpx;
}

.left-slot {
	display: flex;
	flex-direction: row;
	align-items: center;
	padding-left: 30rpx;
	
	.text {
		margin-left: 10rpx;
	}
}
</style>
