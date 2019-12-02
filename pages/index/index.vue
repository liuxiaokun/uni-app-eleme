<template>
	<view>
		<view class="uni-tab-bar">
			<scroll-view scroll-x class="uni-swiper-tab">
				<block v-for="(item, index) in menuList" :key="item.id">
					<view class="swiper-tab-list" :class="{'active':currentMenuIndex === index}" @tap="currentMenuIndex = index">
						{{item.name}}
					</view>
				</block>
			</scroll-view>
		</view>

		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item>
				<image src="/static/dish/1.jpg" mode="scaleToFill"></image>
			</swiper-item>
			<swiper-item>
				<image src="/static/dish/2.jpg" mode="scaleToFill"></image>
			</swiper-item>
			<swiper-item>
				<image src="/static/dish/3.jpg" mode="scaleToFill"></image>
			</swiper-item>
		</swiper>
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in list" :key="index">
				<view class="uni-media-list">
					<image class="uni-media-list-logo logo" :src="item.img"></image>
					<view class="uni-media-list-body body">
						<view class="uni-media-list-text-top">{{item.title}}</view>
						<view class="uni-media-list-text-top">销量：{{item.soldCount}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">价格：{{item.price}}</view>
					</view>
				</view>
			</view>
		</view>
		<view>{{content}}</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentMenuIndex: 0,
				menuList: [{
						id: "412342424143124",
						name: "凉菜"
					},
					{
						id: "412342424143123",
						name: "热菜"
					},
					{
						id: "412342424143125",
						name: "主食"
					},
					{
						id: "412342424143126",
						name: "套餐"
					},
					{
						id: "412342424143127",
						name: "早餐"
					},
					{
						id: "412342424143128",
						name: "午餐"
					},
					{
						id: "412342424143129",
						name: "晚餐"
					}
				],
				list: [{
						img: '/static/dish/4.png',
						title: '鱼香肉丝',
						soldCount: 321,
						price: '23.99'
					},
					{
						img: '/static/dish/2.jpg',
						title: '酸辣白菜',
						soldCount: 321,
						price: '23.99'
					},
					{
						img: '/static/dish/3.jpg',
						title: '锅包肉',
						soldCount: 321,
						price: '23.99'
					},
					{
						img: '/static/dish/4.png',
						title: '锅包肉',
						price: '23.99'
					},
					{
						img: '/static/dish/1.jpg',
						title: '锅包肉',
						soldCount: 321,
						price: '23.99'
					},
					{
						img: '/static/dish/1.jpg',
						title: '锅包肉',
						soldCount: 321,
						price: '23.99'
					}
				],
				content: ''
			}
		},
		onLoad() {
			this.load()
		},
		methods: {

			load() {
			}
		}
	}
</script>

<style>
	.logo {
		width: 150upx;
		height: 150upx
	}

	.body {
		height: 130upx
	}

	.text-area {
		display: flex;
		justify-content: center;
	}
</style>
