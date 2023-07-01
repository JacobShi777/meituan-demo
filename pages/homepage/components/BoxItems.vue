<template>
	<view >
		<view class="container" v-for="(item, index) in dataList" :key="index" @click="handleClick(item.id)">
			<view class="left">
				<image :src="item.imgPath"></image>
			</view>
			<view class="right">
				<view class="right__title">
					{{ item.title }}
				</view>
				
				<view class="right__info">
					<text style="font-size: 32rpx; font-weight: bold; color: orange;">
						{{ item.rate }}分{{' '}}
					</text>
					<text class="desc">
						月售{{ item.saleNum }}{{' '}}
					</text>
					<text class="desc" v-if="item.pricePerPerson !==null ">
						人均¥{{ item.pricePerPerson }}
					</text>
				</view>
				
				<view class="right__delivery">
					<view class="desc">
						<text>
							起送 ¥{{ item.deliveryAtPrice }}{{' '}}
						</text><text>
							配送 约¥{{ item.deliveryPrice }}
						</text>
					</view><view class="desc">
						<text>
							{{ item.deliveryTime }}分钟{{' '}}
						</text>
						<text>
							{{ item.distance }}
						</text>
					</view>
				</view>
				<view class="right__tags">
					<view class="tags" v-for="(tag, index) in item.tags" :key="index">
						{{ tag }}
					</view>
				</view>
				
				<view class="right__discounts">
					<view v-for="(discount, index) in item.discounts" :key="index"
						class="right__discounts__item">
						<template v-if="getType(discount) === 'string'">
							{{ discount }}
						</template>
						<template v-else>
							<text v-for="(sDiscount, index) in discount" :key="index">
								{{ discount.length === index + 1 ? sDiscount : sDiscount + ' | ' }}
							</text>
						</template>
					</view>
				</view>
			</view>
		</view>
		<view class="bottom-desc" v-if="loading">
			数据加载中...
		</view>
		<view class="bottom-desc" v-if="finish">
			没有更多数据了
		</view>
	</view>
</template>

<script>
	import { boxItems } from '@/constants/boxItems.js'
	export default {
		data() {
			return {
				dataList: [],
				currentPage: 0,
				numPerPage: 4,
				loading: false,
				finish: false,
			};
		},
		created() {
			this.dataList.push(...boxItems)
		},
		methods: {
			handleClick(id) {
				console.log(id)
			},
			getType(v){  
				return typeof v;  
			},
			getData() {
				if (this.finish) return
				
				this.loading = true
				setTimeout(() => {					
					if(this.currentPage === 4) {
						this.finish = true
					} else {
						this.currentPage++
						this.dataList.push(...boxItems)
					}
					this.loading = false
				}, 1000)
			}
		}
	}
</script>

<style lang="scss" scoped>
@import "@/uni_modules/uview-ui/index.scss";

.container {
	height: 230rpx;
	background-color: #ffffff;
	padding: 20rpx;
	margin-top: 20rpx;
	border-radius: 20rpx;
	
	display: flex;
	flex-direction: row;
}

.left {
	width: 230rpx;
	height: 100%;
	
	image {
		width: 100%;
		height: 100%;
		border-radius: 10rpx;
		border: 2rpx solid #f6f6f6;
	}
}

.right {
	padding-left: 20rpx;
	width: calc(100% - 250rpx);
	
	&__title {
		font-size: 38rpx;
		font-weight: bold;
		white-space: nowrap;  
		text-overflow:ellipsis; 
		overflow:hidden;
	}
	
	&__info {
		margin-top: 5rpx;
	}
	
	&__delivery {
		margin-top: 5rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	
	&__tags {
		display: flex;
		flex-direction: row;
		justify-content: left;
		
		.tags {
			font-size: 22rpx;
			color: #DB8F2E;
			background-color: #FEF8E0;
			margin-right: 7rpx;
			padding: 10rpx;
		}
	}
	
	&__discounts {
		display: flex;
		flex-direction: row;
		justify-content: left;
		margin-top: 7rpx;
		
		&__item {			
			color: #D5444F;
			font-size: 20rpx;
			padding: 3rpx 6rpx;
			border: 1rpx solid #D5444F;
			border-radius: 5rpx;
			margin-right: 7rpx;
		}
	}
}

.desc {
	font-size: 24rpx; 
	color: #919191;
}

.bottom-desc {
	font-size: 28rpx;
	color: #919191;
	text-align: center;
	margin-top: 12rpx;
}
</style>
