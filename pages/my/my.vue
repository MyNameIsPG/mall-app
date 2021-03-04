<template>
	<view class="u-wrap">
		<u-navbar title="我的" :background="{ background: '#ff5529' }" titleColor="#fff" :is-back="false" />
		<view class="u-wrap">
			<view class="my-top">
				<view class="head"><text @click="settingBtn" class="icon iconfont icon-shezhi1"></text></view>
				<view class="user-info">
					<view class="portrait"><image src="/static/user-pic.jpg"></image></view>
					<view class="info">
						<view class="nickname"><text>爱跳舞的汤姆</text></view>
						<view class="rank">
							<image src="/static/rank.png"></image>
							<text>v1</text>
						</view>
					</view>
				</view>
				<view class="focus-area">
					<view class="list">
						<view class="num"><text>28</text></view>
						<view class="title"><text>商品关注</text></view>
					</view>
					<view class="list">
						<view class="num"><text>28</text></view>
						<view class="title"><text>喜欢的内容</text></view>
					</view>
					<view class="list">
						<view class="num"><text>28</text></view>
						<view class="title"><text>浏览记录</text></view>
					</view>
				</view>
			</view>
			<!-- 订单信息 -->
			<view class="order">
				<view class="order-title">
					<text class="text">我的订单</text>
					<text class="link">查看全部订单 ></text>
				</view>
				<view class="order-info">
					<view class="list" @click="orderBtn(1)">
						<view class="icon">
							<text class="icon iconfont icon-daifukuan"></text>
							<text class="num">22</text>
						</view>
						<view class="title"><text>待付款</text></view>
					</view>
					<view class="list" @click="orderBtn(1)">
						<view class="icon">
							<text class="icon iconfont icon-weishiyong"></text>
							<!-- <text class="num">22</text> -->
						</view>
						<view class="title"><text>待发货</text></view>
					</view>
					<view class="list" @click="orderBtn(1)">
						<view class="icon">
							<text class="icon iconfont icon-daishouhuo3"></text>
							<!-- <text class="num">22</text> -->
						</view>
						<view class="title"><text>待收货</text></view>
					</view>
					<view class="list" @click="orderBtn(1)">
						<view class="icon">
							<text class="icon iconfont icon-daipinglun1"></text>
							<!-- <text class="num">22</text> -->
						</view>
						<view class="title"><text>评价</text></view>
					</view>
					<view class="list" @click="orderBtn(1)">
						<view class="icon">
							<text class="icon iconfont icon-daifukuan1"></text>
							<!-- <text class="num">22</text> -->
						</view>
						<view class="title"><text>退换</text></view>
					</view>
				</view>
			</view>
			<!-- 钱包 -->
			<view class="wallet-info">
				<view class="list">
					<view class="icon"><text class="number">140</text></view>
					<view class="title"><text>积分</text></view>
				</view>
				<view class="list">
					<view class="icon"><text class="number">2</text></view>
					<view class="title"><text>优惠券</text></view>
				</view>
				<view class="list">
					<view class="icon"><text class="number">200.00</text></view>
					<view class="title"><text>余额</text></view>
				</view>
				<view class="list">
					<view class="icon"><text class="iconfont icon-qianbao1"></text></view>
					<view class="title"><text class="action">我的钱包</text></view>
				</view>
			</view>
			<!-- 我的服务 -->
			<view class="my-service">
				<view class="title"><text>我的服务</text></view>
				<view class="service-list">
					<view class="list">
						<view class="thumb"><text class="icon iconfont icon-fankui51"></text></view>
						<view class="name"><text>意见反馈</text></view>
					</view>
					<view class="list">
						<view class="thumb"><text class="icon iconfont icon-shiliangzhinengduixiangx-copy"></text></view>
						<view class="name"><text>客服热线</text></view>
					</view>
					<view class="list" @click="settingBtn">
						<view class="thumb"><text class="icon iconfont icon-shezhi1"></text></view>
						<view class="name"><text>设置</text></view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		settingBtn() {
			uni.navigateTo({
				url: `/pages/setting/setting`
			});
		},
		orderBtn() {
			uni.navigateTo({
				url: `/pages/myOrderList/myOrderList`
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.my-top {
	position: relative;
	width: 100%;
	height: 300rpx;
	background: #ff5529;
	border-radius: 0 0 50% 50%/0 0 20% 20%;
	.head {
		position: absolute;
		right: 50rpx;
		top: 10rpx;
		color: #ffffff;
		.iconfont {
			font-size: 46rpx;
		}
	}
	.user-info {
		display: flex;
		align-items: center;
		padding: 10px 5% 0;
		.portrait {
			width: 120rpx;
			height: 120rpx;
			margin-right: 20rpx;
			box-sizing: border-box;
			image {
				width: 100%;
				height: 100%;
				border-radius: 100%;
				border: 4rpx solid #ffffff;
				box-sizing: border-box;
			}
		}
		.info {
			display: flex;
			flex-direction: column;
			justify-content: center;
			width: 70%;
			height: 100%;
			.nickname {
				width: 100%;
				padding: 10rpx 0;
				text {
					color: #ffffff;
					font-size: 32rpx;
				}
			}
			.rank {
				display: flex;
				align-items: center;
				width: 120rpx;
				height: 30rpx;
				padding: 0 10rpx;
				border: 2rpx solid #f0ad4e;
				border-radius: 30rpx;
				image {
					width: 24rpx;
					height: 24rpx;
				}
				text {
					font-size: 24rpx;
					color: #ffffff;
					margin-left: 10rpx;
				}
			}
		}
	}
	/* 关注区 */
	.focus-area {
		display: flex;
		align-items: center;
		width: 100%;
		height: 120rpx;
		margin-top: 10px;
		.list {
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			width: 33%;
			height: 100%;
			.num {
				display: flex;
				align-items: center;
				text {
					color: #ffffff;
					font-size: 36rpx;
					font-weight: bold;
				}
			}
			.title {
				display: flex;
				align-items: center;
				margin-top: 5rpx;
				text {
					color: #ffffff;
					font-size: 26rpx;
				}
			}
		}
	}
}
/* 订单信息 */
.order {
	width: 94%;
	margin: 40rpx auto;
	border-radius: 20rpx;
	background-color: #ffffff;
	.order-title {
		height: 80rpx;
		border-bottom: 1px solid #f1f1f1;
		display: flex;
		align-items: center;
		padding: 0 20rpx;
		.text {
			flex: 1;
			font-weight: bold;
			font-size: 26rpx;
		}
		.link {
			color: #999;
		}
	}
	.order-info {
		display: flex;
		height: 200rpx;
		.list {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			width: 20%;
			height: 100%;
			.icon {
				position: relative;
				display: flex;
				align-items: center;
				.iconfont {
					font-size: 58rpx;
					color: #333333;
				}
				.num {
					position: absolute;
					right: -20rpx;
					top: -10rpx;
					font-size: 22rpx;
					width: 40rpx;
					height: 40rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					color: $uni-color-primary;
					border: 2rpx solid $uni-color-primary;
					border-radius: 100%;
					background-color: #ffffff;
				}
			}
			.title {
				display: flex;
				align-items: center;
				margin-top: 10rpx;
				text {
					color: #333333;
					font-size: 26rpx;
				}
			}
		}
	}
}
/* 钱包 */
.wallet-info {
	display: flex;
	width: 94%;
	height: 200rpx;
	border-radius: 20rpx;
	background-color: #ffffff;
	margin: 20rpx auto;
	.list {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 25%;
		height: 100%;
		.icon {
			position: relative;
			display: flex;
			height: 74rpx;
			align-items: center;
			.iconfont {
				font-size: 54rpx;
				color: $uni-color-primary;
			}
			.number {
				font-size: 32rpx;
				color: #212121;
				font-weight: bold;
			}
		}
		.title {
			display: flex;
			align-items: center;
			margin-top: 10rpx;
			text {
				color: #333333;
				font-size: 26rpx;
			}
		}
	}
}
/* 我的服务 */
.my-service {
	width: 94%;
	margin: 40rpx auto;
	border-radius: 20rpx;
	background-color: #ffffff;
	.title {
		height: 80rpx;
		border-bottom: 1px solid #f1f1f1;
		display: flex;
		align-items: center;
		padding: 0 20rpx;
		text {
			font-weight: bold;
			font-size: 26rpx;
		}
	}
	.service-list {
		display: flex;
		flex-wrap: wrap;
		height: 200rpx;
		.list {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			width: 25%;
			height: 200rpx;
			.thumb {
				.iconfont {
					font-size: 54rpx;
				}
			}
			.name {
				display: flex;
				align-items: center;
				justify-content: center;
				margin-top: 10rpx;
				text {
					color: #212121;
					font-size: 26rpx;
				}
			}
		}
	}
}
</style>
