<template>
	<view class="tab-bar">
		<view class="tab-item" :class="{'active-tab': active === 'home'}" hover-class="tab-hover" hover-stay-time="70" @click="goToPage('home')">
			<uni-icons type="home" size="24" :color="active === 'home' ? '#4285f4' : '#888'"></uni-icons>
			<text class="tab-text">发布</text>
			<view class="tab-line" v-if="active === 'home'"></view>
		</view>
		<view class="tab-item" :class="{'active-tab': active === 'orders'}" hover-class="tab-hover" hover-stay-time="70" @click="goToPage('orders')">
			<uni-icons type="list" size="24" :color="active === 'orders' ? '#4285f4' : '#888'"></uni-icons>
			<text class="tab-text">订单</text>
			<view class="tab-line" v-if="active === 'orders'"></view>
		</view>
		<view class="tab-item" :class="{'active-tab': active === 'my'}" hover-class="tab-hover" hover-stay-time="70" @click="goToPage('my')">
			<uni-icons type="person" size="24" :color="active === 'my' ? '#4285f4' : '#888'"></uni-icons>
			<text class="tab-text">我的</text>
			<view class="tab-line" v-if="active === 'my'"></view>
		</view>
	</view>
</template>

<script>
	import uniIcons from '@/uni_modules/uni-icons/components/uni-icons/uni-icons.vue'
	
	export default {
		name: 'TabBar',
		components: {
			uniIcons
		},
		props: {
			active: {
				type: String,
				default: 'home' // 默认激活首页
			}
		},
		methods: {
			goToPage(page) {
				// 如果已经在当前页面，则不跳转
				if (page === this.active) return;
				
				// 根据页面跳转到对应路径
				switch(page) {
					case 'home':
						uni.reLaunch({
							url: '/pages/index/index'
						});
						break;
					case 'orders':
						uni.reLaunch({
							url: '/pages/orders/orders'
						});
						break;
					case 'my':
						uni.reLaunch({
							url: '/pages/my/my'
						});
						break;
				}
			}
		}
	}
</script>

<style>
	/* 底部导航 */
	.tab-bar {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		height: 100rpx;
		display: flex;
		background-color: #fff;
		border-top-left-radius: 30rpx;
		border-top-right-radius: 30rpx;
		border-top: 1rpx solid #f0f0f0;
		box-shadow: 0 -2rpx 10rpx rgba(0, 0, 0, 0.05);
		z-index: 999;
	}
	
	.tab-item {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		position: relative;
		padding-top: 15rpx;
		padding-bottom: 10rpx;
	}
	
	.tab-text {
		font-size: 24rpx;
		color: #888;
		margin-top: 8rpx;
	}
	
	.active-tab .tab-text {
		color: #4285f4;
	}
	
	.tab-line {
		position: absolute;
		bottom: 0;
		width: 45rpx;
		height: 6rpx;
		background-color: #4285f4;
		border-radius: 3rpx;
	}
	
	.tab-hover {
		background-color: rgba(0, 0, 0, 0.05);
	}
</style>