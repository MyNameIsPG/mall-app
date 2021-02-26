<template>
	<view class="u-wrap">
		<view class="my-top">
			<view class="head">
				<text class="text">共1件宝贝</text>
				<text class="btns">
					<text class="icon iconfont icon-post"></text>
					编辑购物车
				</text>
			</view>
		</view>

		<view class="cart-list">
			<view class="item">
				<view class="checkbox-icon"><text class="icon iconfont icon-roundcheck"></text></view>
				<view class="content">
					<view class="img-pic"><image src="/static/pms-pic/goods_thumb_01.png"></image></view>
					<view class="content-right">
						<view class="content-right-title">薇妮(Viney)时尚包包女包牛皮单肩包女休闲百搭斜挎包韩版小方包潮(水电费枪色)</view>
						<view class="content-right-nums">
							<view class="price">￥80</view>
							<view class="pedometer"><u-number-box v-model="value"></u-number-box></view>
						</view>
					</view>
				</view>
			</view>
			<view class="item" v-for="item in 20" :key="item">
				<view class="checkbox-icon"><text class="icon iconfont icon-round"></text></view>
				<view class="content">
					<view class="img-pic"><image src="/static/pms-pic/goods_thumb_01.png"></image></view>
					<view class="content-right">
						<view class="content-right-title">薇妮(Viney)时尚包包女包牛皮单肩包女休闲百搭斜挎包韩版小方包潮(水电费枪色)</view>
						<view class="content-right-nums">
							<view class="price">￥80</view>
							<view class="pedometer"><u-number-box v-model="value"></u-number-box></view>
						</view>
					</view>
				</view>
			</view>
		</view>

		<u-back-top :scroll-top="scrollTop"></u-back-top>
		<view class="navigation">
			<view class="left">
				<view class="item">
					<view class="text u-line-1">
						<text class="icon iconfont icon-round"></text>
						全选
					</view>
				</view>
			</view>
			<view class="right">
				<view style="font-size: 30rpx;margin-right: 20rpx;">
					合计：
					<text style="color: red;font-weight: bold;">
						￥
						<text style="font-size: 36rpx;">0</text>
					</text>
				</view>
				<view class="buy btn u-line-1">去下单</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: 'cartData',
	data() {
		return {
			scrollTop: 0,
			value: 0
		};
	},
	onPageScroll(e) {
		this.scrollTop = e.scrollTop;
	}
};
</script>

<style lang="scss" scoped>
.my-top {
	position: fixed;
	width: 100%;
	height: 140px;
	background: #ff5529;
	border-radius: 0 0 50% 50%/0 0 20% 20%;
	.head {
		position: absolute;
		top: 22rpx;
		left: 0px;
		display: flex;
		width: 100%;
		padding: 0 28rpx;
		color: #fff;
		font-size: 28rpx;
		.text {
			flex: 1;
			color: #eee;
		}
		.btns {
			flex: 1;
			text-align: right;
			.iconfont {
				margin-right: 6rpx;
			}
		}
	}
}
.cart-list {
	position: absolute;
	top: 50px;
	left: 0px;
	right: 0px;
	z-index: 99;
	padding: 0 30rpx;
	overflow: auto;
	bottom: 45px;
	.item {
		background: #fff;
		border-radius: 20rpx;
		display: flex;
		padding: 20rpx;
		box-sizing: border-box;
		margin-bottom: 20rpx;
		.checkbox-icon {
			width: 50rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			margin-right: 20rpx;
			.iconfont {
				font-size: 18px;
			}
			.icon-roundcheck {
				color: $uni-color-primary;
			}
		}
		.content {
			flex: 1;
			display: flex;
			.img-pic {
				width: 140rpx;
				height: 140rpx;
				image {
					width: 100%;
					height: 100%;
				}
			}
			.content-right {
				flex: 1;
				margin-left: 30rpx;
				.content-right-title {
					display: -webkit-box;
					-webkit-line-clamp: 2;
					overflow: hidden;
					text-overflow: ellipsis;
					-webkit-box-orient: vertical;
					font-size: 13px;
					color: #212121;
				}
				.content-right-nums {
					display: flex;
					align-items: center;
					margin-top: 20rpx;
					.price {
						flex: 1;
						color: $uni-color-primary;
					}
					.pedometer {
						flex: 1;
					}
				}
			}
		}
	}
}
.navigation {
	display: flex;
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
	color: #ffffff;
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
