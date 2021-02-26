<template>
	<view class="u-wrap">
		<view class="page-box">
			<view><no-cart></no-cart></view>
			<view class="u-text-center"><image style="width: 208px; height: 20px;" src="/static/wntj_title.png"></image></view>
		</view>
		<view class="wrap">
			<u-waterfall v-model="flowList" ref="uWaterfall">
				<template v-slot:left="{ leftList }">
					<view class="demo-warter" v-for="(item, index) in leftList" :key="index">
						<!-- 警告：微信小程序中需要hx2.8.11版本才支持在template中结合其他组件，比如下方的lazy-load组件 -->
						<u-lazy-load threshold="-150" border-radius="10" :image="item.image" :index="index"></u-lazy-load>
						<view class="demo-title">{{ item.title }}</view>
						<view class="demo-price">{{ item.price }}元</view>
						<view class="demo-tag">
							<view class="demo-tag-owner">自营</view>
							<view class="demo-tag-text">放心购</view>
						</view>
						<view class="demo-shop">{{ item.shop }}</view>
						<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
					</view>
				</template>
				<template v-slot:right="{ rightList }">
					<view class="demo-warter" v-for="(item, index) in rightList" :key="index">
						<u-lazy-load threshold="-150" border-radius="10" :image="item.image" :index="index"></u-lazy-load>
						<view class="demo-title">{{ item.title }}</view>
						<view class="demo-price">{{ item.price }}元</view>
						<view class="demo-tag">
							<view class="demo-tag-owner">自营</view>
							<view class="demo-tag-text">放心购</view>
						</view>
						<view class="demo-shop">{{ item.shop }}</view>
						<u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
					</view>
				</template>
			</u-waterfall>
			<u-loadmore bg-color="rgb(240, 240, 240)" :status="loadStatus" @loadmore="addRandomData"></u-loadmore>
		</view>
		<u-back-top :scroll-top="scrollTop"></u-back-top>
	</view>
</template>

<script>
import noCart from './noCart.vue';
export default {
	name: 'cart',
	components: {
		noCart
	},
	data() {
		return {
			scrollTop: 0,
			loadStatus: 'loadmore',
			flowList: [],
			list: [
				{
					price: 35,
					title: '北国风光，千里冰封，万里雪飘',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23327_s.jpg'
				},
				{
					price: 75,
					title: '望长城内外，惟余莽莽',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23325_s.jpg'
				},
				{
					price: 385,
					title: '大河上下，顿失滔滔',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/hpic2119_s.jpg'
				},
				{
					price: 784,
					title: '欲与天公试比高',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23369_s.jpg'
				},
				{
					price: 7891,
					title: '须晴日，看红装素裹，分外妖娆',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/hpic2130_s.jpg'
				},
				{
					price: 2341,
					shop: '李白杜甫白居易旗舰店',
					title: '江山如此多娇，引无数英雄竞折腰',
					image: '/static/pic-bg/zzpic23346_s.jpg'
				},
				{
					price: 661,
					shop: '李白杜甫白居易旗舰店',
					title: '惜秦皇汉武，略输文采',
					image: '/static/pic-bg/zzpic23344_s.jpg'
				},
				{
					price: 1654,
					title: '唐宗宋祖，稍逊风骚',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23343_s.jpg'
				},
				{
					price: 1678,
					title: '一代天骄，成吉思汗',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23343_s.jpg'
				},
				{
					price: 924,
					title: '只识弯弓射大雕',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23343_s.jpg'
				},
				{
					price: 8243,
					title: '俱往矣，数风流人物，还看今朝',
					shop: '李白杜甫白居易旗舰店',
					image: '/static/pic-bg/zzpic23343_s.jpg'
				}
			]
		};
	},
	onPageScroll(e) {
		this.scrollTop = e.scrollTop;
	},
	created() {
		this.addRandomData();
	},
	methods: {
		addRandomData() {
			let arr = [];
			for (let i = 0; i < 10; i++) {
				let index = this.$u.random(0, this.list.length - 1);
				// 先转成字符串再转成对象，避免数组对象引用导致数据混乱
				let item = JSON.parse(JSON.stringify(this.list[index]));
				item.id = this.$u.guid();
				arr.push(item);
			}
			this.flowList = [...this.flowList, ...arr];
		},
		remove(id) {
			this.$refs.uWaterfall.remove(id);
		}
	},
	onReachBottom() {
		this.loadStatus = 'loading';
		// 模拟数据加载
		setTimeout(() => {
			this.loadStatus = 'loadmore';
			this.addRandomData();
		}, 1000);
	}
};
</script>

<style lang="scss" scoped>
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
