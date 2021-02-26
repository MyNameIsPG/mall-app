<template>
	<view class="u-wrap">
		<!-- 用户信息 -->
		<view class="user-info">
			<view class="user-data">
				<view class="portrait-nickname">
					<view class="portrait"><image src="/static/user-pic.jpg" mode=""></image></view>
					<view class="nickname"><text>爱跳舞的汤姆猫</text></view>
				</view>
				<view class="more"><text class="icon iconfont icon-arrow-right"></text></view>
			</view>
		</view>
		<!-- 设置列表 -->
		<view class="setting-list">
			<view class="list">
				<view class="title"><text>地址管理</text></view>
				<view class="more-content">
					<text class="content">地址管理</text>
					<text class="more icon iconfont icon-arrow-right"></text>
				</view>
			</view>
			<view class="list">
				<view class="title"><text>账户安全</text></view>
				<view class="more-content">
					<text class="content">密码/支付等管理</text>
					<text class="more icon iconfont icon-arrow-right"></text>
				</view>
			</view>
			<view class="list">
				<view class="title"><text>商城会员</text></view>
				<view class="more-content">
					<text class="content">会员专属商品</text>
					<text class="more icon iconfont icon-arrow-right"></text>
				</view>
			</view>
		</view>
		<!-- 设置列表 -->
		<view class="setting-list">
			<view class="list">
				<view class="title"><text>通用</text></view>
				<view class="more-content">
					<text class="content">清除本地缓存等</text>
					<text class="more icon iconfont icon-arrow-right"></text>
				</view>
			</view>
			<view class="list">
				<view class="title"><text>关于我们</text></view>
				<view class="more-content">
					<text class="content"></text>
					<text class="more icon iconfont icon-arrow-right"></text>
				</view>
			</view>
		</view>
		<!-- 退出 -->
		<view class="quit-login"><text>退出登录</text></view>
	</view>
</template>

<script>
export default {
	name: 'setting',
	data() {
		return {};
	},
	methods: {}
};
</script>

<style lang="scss" scoped>
/* 用户信息 */
.user-info {
	width: 100%;
	background-color: #ffffff;
	.user-data {
		display: flex;
		align-items: center;
		padding: 0 4%;
		height: 140rpx;
		.portrait-nickname {
			display: flex;
			align-items: center;
			width: 100%;
			height: 90%;
			.portrait {
				width: 120rpx;
				height: 120rpx;
				image {
					width: 100%;
					height: 100%;
					border-radius: 100%;
				}
			}
			.nickname {
				display: flex;
				align-items: center;
				margin-left: 20rpx;
				height: 140rpx;
				text {
					font-size: 28rpx;
					color: #222222;
				}
			}
		}
		.more {
			display: flex;
			align-items: center;
			text {
				color: #959595;
			}
		}
	}
}

/* 设置列表 */
.setting-list {
	padding: 0 4%;
	background-color: #ffffff;
	margin: 20rpx auto;
	.list {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		height: 100rpx;
		border-bottom: 2rpx solid #f6f6f6;
		&:last-child {
			border-bottom: none;
		}
		.title {
			display: flex;
			align-items: center;
			text {
				font-size: 28rpx;
				color: #222222;
			}
		}
		.more-content {
			display: flex;
			align-items: center;
			.content {
				font-size: 28rpx;
				color: #959595;
			}
			.more {
				color: #959595;
				margin-left: 20rpx;
			}
		}
	}
}

/* 退出登录 */
.quit-login {
	position: fixed;
	left: 0;
	bottom: 0;
	display: flex;
	align-items: center;
	justify-content: center;
	width: 100%;
	height: 100rpx;
	background: #ffffff;
	text {
		color: #222222;
		font-size: 28rpx;
	}
}
</style>
