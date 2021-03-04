<template>
	<view>
		<u-navbar :background="{ background: '#ff5529' }" titleColor="#fff" :is-back="false">
			<view class="slot-wrap">
				<view class="search-wrap">
					<!-- 如果使用u-search组件，必须要给v-model绑定一个变量 -->
					<u-search v-model="keyword" :show-action="showAction" height="56" :action-style="{color: '#fff'}"></u-search>
				</view>
			</view>
			<view class="navbar-right" slot="right">
				<view class="message-box right-item">
					<u-icon name="chat" size="38"></u-icon>
					<u-badge count="18" size="mini" :offset="[-15, -15]"></u-badge>
				</view>
			</view>
		</u-navbar>
		<view  class="wrap" style="background: #FFFFFF;">
			<!-- banner -->
			<view class="banner" style="padding: 20rpx; box-sizing: border-box;">
				<u-swiper :list="list" height="300"></u-swiper>
			</view>
			<!-- 菜单导航 -->
			<view class="menu-nav">
				<scroll-view scroll-x @scroll="ScrollMenu" class="nav-list">
					<view class="nav" ref="nav" :style="navList.length<=10?'flex-direction:row':''">
						<view class="list" v-for="(item,index) in navList"
						@click="onSkip('menu')"
						:key="item.id">
							<image :src="'/static/nav/nav_ico'+(index+1)+'.png'" mode=""></image>
							<text>{{item.name}}</text>
						</view>
					</view>
				</scroll-view>
				<view class="indicator" v-if="navList.length>10">
					<view class="plan">
						<view class="bar" :style="'left:'+slideNum+'%'"></view>
					</view>
				</view>
			</view>
			<!-- 限时抢购，好货精选 -->
			<view class="flash-good">
				<view class="flash-sale">
					<view class="line"></view>
					<view class="flash-title">
						<view class="pictrue">
							<image src="/static/xsqg_title.png" mode=""></image>
						</view>
						<view class="date-time">
							<text class="time">02</text>
							<text class="da">:</text>
							<text class="time">15</text>
							<text class="da">:</text>
							<text class="time">55</text>
						</view>
					</view>
					<view class="goods-list">
						<view class="list">
							<view class="pictrue">
								<image src="/static/goods/goods_01.png"></image>
							</view>
							<view class="price">
								<text class="selling-price">￥59</text>
								<text class="original-price">￥999</text>
							</view>
						</view>
						<view class="list">
							<view class="pictrue">
								<image src="/static/goods/goods_02.png"></image>
							</view>
							<view class="price">
								<text class="selling-price">￥59</text>
								<text class="original-price">￥999</text>
							</view>
						</view>
					</view>
				</view>
				<view class="good-choice">
					<view class="goods-title">
						<view class="title">
							<text>好货精选</text>
						</view>
						<view class="describe">
							<text>全场</text>
							<text class="num">1</text>
							<text>折起</text>
						</view>
					</view>
					<view class="goods-list">
						<view class="list">
							<view class="pictrue">
								<image src="/static/goods/goods_03.png"></image>
							</view>
							<view class="price">
								<text class="selling-price">￥59</text>
								<text class="original-price">￥999</text>
							</view>
						</view>
						<view class="list">
							<view class="pictrue">
								<image src="/static/goods/goods_08.png"></image>
							</view>
							<view class="price">
								<text class="selling-price">￥59</text>
								<text class="original-price">￥999</text>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keyword: "",
				showAction: false,
				CustomBar: this.CustomBar,
				list: [
					{
						image: '/static/banner/banner_01.png'
					},
					{
						image: '/static/banner/banner_02.png'
					},
					{
						image: '/static/banner/banner_03.png'
					},
					{
						image: '/static/banner/banner_04.png'
					},
				],
				navList: [
								{
									id: 1,
									name: '手机专区',
								},{
									id: 2,
									name: '潮牌男装',
								},{
									id: 3,
									name: '运动男装',
								},{
									id: 4,
									name: '时尚背包',
								},{
									id: 5,
									name: '台式电脑',
								},{
									id: 6,
									name: '珠宝首饰',
								},{
									id: 7,
									name: '美颜美妆',
								},{
									id: 8,
									name: '家用电器',
								},{
									id: 9,
									name: '洗护用品',
								},{
									id: 10,
									name: '台式电脑',
								}
							],
			}
		},
		onLoad() {

		},
		methods: {
			ScrollMenu(e){
					let scrollLeft = e.target.scrollLeft;
					const query = uni.createSelectorQuery().in(this);
					query.select('.nav').boundingClientRect(data => {
						let wid = e.target.scrollWidth - data.width - (data.left*2+5);
						this.slideNum = (scrollLeft/wid*300) / 2;
					}).exec();
				},	
		}
	}
</script>

<style lang="scss" scoped>
	.navbar-right {
			margin-right: 24rpx;
			display: flex;
		}
		
		.search-wrap {
			margin: 0 20rpx;
			flex: 1;
		}
		
		.right-item {
			margin: 0 12rpx;
			position: relative;
			color: #ffffff;
			display: flex;
		}
		
		.message-box {
			
		}
		
		.slot-wrap {
			display: flex;
			align-items: center;
			flex: 1;
		}
		
		.map-wrap {
			display: flex;
			align-items: center;
			padding: 4px 6px;
			background-color: rgba(240,240, 240, 0.35);
			color: #fff;
			font-size: 22rpx;
			border-radius: 100rpx;
			margin-left: 30rpx;
		}
		
		.map-wrap-text {
			padding: 0 6rpx;
		}
	/* 菜单导航 */
	.menu-nav{
		position: relative;
		width: 100%;
		height: 300rpx;
		margin:30rpx auto;
		.nav-list{
			white-space: nowrap; 
			height: 270rpx;
			width: 100%;
			.nav{
				display: inline-block;
				display: flex;
				flex-direction: column;
				flex-wrap: wrap;
				justify-content: space-between;
				height: 270rpx;
			}
			.list{
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				width: 20%;
				height: 130rpx;
				margin-bottom: 20rpx;
				image{
					width: 75rpx;
					height: 75rpx;
					border-radius: 100%;
				}
				text{
					font-size: 26rpx;
					color: #363636;
					margin-top: 10rpx;
				}
			}
		}
		
	}
	/* 通知 */
	.inform{
		padding: 0 25rpx;
		height: 130rpx;
		// margin: 30rpx auto;
		border-bottom: 16rpx solid #f9f9f9;
		.inform-info{
			display: flex;
			padding: 0 20rpx;
			height: 70rpx;
			background-color: #f7f7f7;
			border-radius: 10rpx;
			.picture{
				width: 20%;
				height: 100%;
				image{
					width: 93rpx;
					height: 84rpx;
					margin-top: -20rpx;
				}
			}
			.info{
				width: 80%;
				height: 100%;
				.swiper{
					width: 100%;
					height: 100%;
					.swiper-item{
						display: flex;
						align-items: center;
						width: 100%;
						height: 100%;
						text{
							font-size: 28rpx;
							color: #848281;
						}
					}
				}
			}
		}
	}	
	/* 限时抢购，好货精选 */
	.flash-good{
		display: flex;
		align-items: center;
		padding: 0 25rpx;
		height: 320rpx;
		background-color: #FFFFFF;
		border-bottom: 16rpx solid #f9f9f9;
		.flash-sale{
			position: relative;
			width: 50%;
			height: 100%;
			.line{
				position: absolute;
				right: 0;
				top: 50%;
				width: 2rpx;
				height: 80%;
				background-color: #f9f9f9;
				transform: translate(0,-50%);
			}
			.flash-title{
				display: flex;
				align-items: center;
				// justify-content: space-between;
				width: 100%;
				height: 80rpx;
				.pictrue{
					display: flex;
					align-items: center;
					height: 100%;
					image{
						width: 118rpx;
						height: 28rpx;
					}
				}
				.date-time{
					display: flex;
					align-items: center;
					margin-left: 50rpx;
					.time{
						display: flex;
						align-items: center;
						justify-content: center;
						width: 40rpx;
						height: 40rpx;
						background-color: red;
						font-size: 24rpx;
						color: #FFFFFF;
						border-radius: 6rpx;
					}
					.da{
						font-size: 34rpx;
						color: #212121;
						margin: 0 6rpx;
					}
				}
			}
			.goods-list{
				display: flex;
				width: 100%;
				height: 220rpx;
				.list{
					width: 50%;
					height: 100%;
					.pictrue{
						width: 100%;
						height: 70%;
						image{
							width: 150rpx;
							height: 150rpx;
						}
					}
					.price{
						display: flex;
						align-items: center;
						width: 100%;
						height: 30%;
						.selling-price{
							font-size: 28rpx;
							font-weight: bold;
							color: red;
						}
						.original-price{
							font-size: 24rpx;
							text-decoration: line-through;
							color: #bbbaba;
							margin-left: 10rpx;
						}
					}
				}
			}
		}
		.good-choice{
			width: 50%;
			height: 100%;
			.goods-title{
				display: flex;
				align-items: center;
				padding: 0 20rpx;
				height: 80rpx;
				.title{
					display: flex;
					align-items: center;
					text{
						font-size: 28rpx;
						color: #4c4b4b;
					}
				}
				.describe{
					display: flex;
					align-items: center;
					margin-left: 10rpx;
					text{
						font-size: 24rpx;
						color: #979696;
					}
					.num{
						display: flex;
						align-items: center;
						justify-content: center;
						margin: 0 6rpx;
						width: 30rpx;
						height: 30rpx;
						background-color: red;
						color: #FFFFFF;
						border-radius: 6rpx;
					}
				}
			}
			.goods-list{
				display: flex;
				width: 100%;
				height: 220rpx;
				.list{
					width: 50%;
					height: 100%;
					.pictrue{
						width: 100%;
						height: 70%;
						image{
							width: 150rpx;
							height: 150rpx;
						}
					}
					.price{
						display: flex;
						align-items: center;
						width: 100%;
						height: 30%;
						.selling-price{
							font-size: 28rpx;
							font-weight: bold;
							color: red;
						}
						.original-price{
							font-size: 24rpx;
							text-decoration: line-through;
							color: #bbbaba;
							margin-left: 10rpx;
						}
					}
				}
			}
		}
	}
	/* 今日上新 */
	.new-product{
		padding: 0 25rpx;
		height: 350rpx;
		.product-title{
			display: flex;
			align-items: center;
			justify-content: space-between;
			width: 100%;
			height: 100rpx;
			.title{
				display: flex;
				align-items: center;
				image{
					width: 24rpx;
					height: 32rpx;
				}
				text{
					font-size: 30rpx;
					color: #4c4b4b;
					margin-left: 20rpx;
				}
			}
			.describe{
				display: flex;
				align-items: center;
				text{
					font-size: 26rpx;
					color: #a09f9f;
				}
			}
		}
		.goods-list{
			white-space:nowrap;
			width: 100%;
			height: 220rpx;
			overflow-y: hidden;
			overflow-x: auto;
			.list{
				display:inline-block;
				width: 25%;
				height: 100%;
				margin-right: 20rpx;
				.pictrue{
					width: 100%;
					height: 70%;
					image{
						width: 150rpx;
						height: 150rpx;
					}
				}
				.price{
					display: flex;
					align-items: center;
					width: 100%;
					height: 30%;
					.selling-price{
						font-size: 28rpx;
						font-weight: bold;
						color: red;
					}
					.original-price{
						font-size: 24rpx;
						text-decoration: line-through;
						color: #bbbaba;
						margin-left: 10rpx;
					}
				}
			}
		}
		
	}
</style>
