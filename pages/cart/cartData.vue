<template>
	<view class="u-wrap">
		
		
		<u-back-top :scroll-top="scrollTop"></u-back-top>
		<view class="navigation">
			<view class="left">
				<view class="item">
					<view class="text u-line-1"><text class="icon iconfont icon-round"></text> 全选</view>
				</view>
			</view>
			<view class="right">
				<view style="font-size: 30rpx;margin-right: 20rpx;">
					合计：<text style="color: red;font-weight: bold;">￥<text style="font-size: 36rpx;">0</text></text>
				</view>
				<view class="buy btn u-line-1">去下单</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: "cartData",
	data() {
		return {
			scrollTop: 0,
		}
	},
	onPageScroll(e) {
		this.scrollTop = e.scrollTop;
	}
};
</script>

<style>
	page {
		background: #EEEEEE;
	}
</style>
<style lang="scss" scoped>
	
	.navigation {
		display: flex;
		border: solid 2rpx #f2f2f2;
		background-color: #ffffff;
		padding: 16rpx;
		position: fixed;
		left: 0px;
		z-index: 999;
		bottom: 1px;
		right: 0px;
		.left {
			font-size: 20rpx;
			flex: 1;
			display: flex;
			align-items: center;
			.item {
				margin: 0 30rpx;
				font-size: 12px;
				.text {
					display: flex;
					align-items: center;
					.icon {
						margin-right: 4px;
						font-size: 18px;
						color: #333;
					}
				}
			}
		}
		.right {
			display: flex;
			font-size: 28rpx;
			align-items: center;
			flex: 1;
			text-align: right;
			justify-content: flex-end;
			.btn {
				line-height: 66rpx;
				padding: 0 30rpx;
				border-radius: 36rpx;
				color: #ffffff;
			}
			.cart {
				background-color: #ed3f14;
				margin-right: 30rpx;
			}
			.buy {
				background-color: #ff7900;
			}
		}
	}
	.demo-warter {
		border-radius: 8px;
		margin: 5px;
		background-color: #ffffff;
		padding: 8px;
		position: relative;
	}
	
	.u-close {
		position: absolute;
		top: 32rpx;
		right: 32rpx;
	}
	
	.demo-image {
		width: 100%;
		border-radius: 4px;
	}
	
	.demo-title {
		font-size: 30rpx;
		margin-top: 5px;
		color: $u-main-color;
	}
	
	.demo-tag {
		display: flex;
		margin-top: 5px;
	}
	
	.demo-tag-owner {
		background-color: $u-type-error;
		color: #FFFFFF;
		display: flex;
		align-items: center;
		padding: 4rpx 14rpx;
		border-radius: 50rpx;
		font-size: 20rpx;
		line-height: 1;
	}
	
	.demo-tag-text {
		border: 1px solid $u-type-primary;
		color: $u-type-primary;
		margin-left: 10px;
		border-radius: 50rpx;
		line-height: 1;
		padding: 4rpx 14rpx;
		display: flex;
		align-items: center;
		border-radius: 50rpx;
		font-size: 20rpx;
	}
	
	.demo-price {
		font-size: 30rpx;
		color: $u-type-error;
		margin-top: 5px;
	}
	
	.demo-shop {
		font-size: 22rpx;
		color: $u-tips-color;
		margin-top: 5px;
	}
</style>
