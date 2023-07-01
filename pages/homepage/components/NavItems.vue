<template>
	<view class="nav-items-comp">
		<swiper
				:indicator-dots="true"
				class="swiper"
		>
			<swiper-item>
				<!-- <button @click="demoClick">demoClick</button> -->
				<u-grid :border="false" col="5">
					<u-grid-item
							v-for="(item, index) in swiperList.slice(0, 7)"
							:index="index"
							:key="index"
							@click="handleClick(item.value)"
					>
						<u-image :src="`/static/image/homepage/${item.imgName}`" 
							height="70rpx" width="70rpx" mode=""></u-image>
						<text class="grid-text">{{ item.label }}</text>
					</u-grid-item>
				</u-grid>
			</swiper-item>
			<swiper-item>
				<u-grid :border="true"  col="5">
					<u-grid-item
							v-for="(item, index) in swiperList.slice(7)"
							:index="index + 9"
							:key="index"
							@click="handleClick(item.value)"
					>
						<u-image :src="`/static/image/homepage/${item.imgName}`"
							height="70rpx" width="70rpx" mode=""></u-image>
						<text class="grid-text">{{ item.label }}</text>
					</u-grid-item>
				</u-grid>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	import { displayItems } from '@/constants/displayItems.js'
	export default {
		data() {
			return {
				// swiperList: ['integral', 'kefu-ermai', 'coupon', 'gift', 'scan', 'pause-circle', 'wifi', 'email', 'list'],
				// swiperList: ['美食', '甜品', '色块－超市', '蔬菜区', '代办买药', '午餐', '券', '小吃', '日料'],
				swiperList: []
			};
		},
		created() {
			this.swiperList = displayItems
		},
		methods: {
			handleClick(val) {
				console.log(val)
				uni.navigateTo({
					url: `/pages/display/${val}/${val}`
				})
			},
			demoClick() {
				console.log(displayItems)
				
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import "@/uni_modules/uview-ui/index.scss";
	
.nav-items-comp {
	margin-top: 20rpx
}

/deep/ ::-webkit-scrollbar {
			width: 4px !important;
			height: 1px !important;
			overflow: auto !important;
			background: transparent !important;
			-webkit-appearance: auto !important;
			display: block;
		}

.swiper {
        // height: 720rpx;
    }

    .grid-text {
        font-size: 14px;
        color: #909399;
        padding: 10rpx 0 20rpx 0rpx;
        /* #ifndef APP-PLUS */
        box-sizing: border-box;
        /* #endif */
    }
</style>
