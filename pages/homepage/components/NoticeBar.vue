<template>
	<view>
		<view>
			<swiper
				class="swiper"
				:indicator-dots="false"
				:autoplay="true"
				:interval="2000"
				:vertical="true"
				:circular="true"
			>
				<swiper-item>
					<view class="outer">						
						<view class="left">
							<u-image src="/static/image/homepage/鸡蛋.png"
								height="50rpx" width="50rpx"></u-image>
							{{text1}}
						</view>
						<view class="right">
							<u-button type="warning" :plain="true" :hairline="true" 
								size="mini" text="去签到" @click="handleClick('去签到')"></u-button>
						</view>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="outer">
						
						<view class="left">						
							<u-image src="/static/image/homepage/鸡蛋.png"
								height="50rpx" width="50rpx"></u-image>
							{{text2}}
						</view>
						<view class="right">
							<u-button type="warning" :plain="true" :hairline="true" 
								size="mini" text="领取" @click="handleClick('领取')"></u-button>
						</view>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text1: '连续签到第2天，可得10米粒',
				text2: '2天下2单美食外卖，赚400米粒'
			};
		},
		methods: {
			handleClick(val) {
				console.log(val)
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import "@/uni_modules/uview-ui/index.scss";
	
.swiper {
	height: 60rpx;
	line-height: 60rpx;
	background-color: #ffffff;
	border-radius: 20rpx;
	font-size: 18rpx;
	
	.outer {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	
	.left {
		display: flex;
		flex-direction: row;
	}
	
	.right {
		margin-right: 20rpx;
	}
}
</style>
