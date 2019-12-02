<template>
	<view>
		
		<view class="uni-product-list">
			<view class="uni-product" v-for="(product,index) in productList" :key="index">
				<view class="image-view">
					<image v-if="renderImage" class="uni-product-image" :src="product.image"></image>
				</view>
				<view class="uni-product-title">{{product.title}}</view>
				<view class="uni-product-price">
					<text class="uni-product-price-favour">￥{{product.originalPrice}}</text>
					<text class="uni-product-price-original">￥{{product.favourPrice}}</text>
					<text class="uni-product-tip">{{product.tip}}</text>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				data: [],
				renderImage:true,
				productList:[
					{
						image:'/static/dish/4.png',
						title:'鱼香肉丝',
						originalPrice:32,
						favourPrice:22,
						tip:'酸辣'
					},
					{
						image:'/static/dish/3.jpg',
						title:'老福山炸肉',
						originalPrice:32,
						favourPrice:22,
						tip:'不辣哦'
					},
					{
						image:'/static/dish/4.png',
						title:'鱼香肉丝',
						originalPrice:32,
						favourPrice:22,
						tip:'酸辣'
					},
					{
						image:'/static/dish/3.jpg',
						title:'老福山炸肉',
						originalPrice:32,
						favourPrice:22,
						tip:'不辣哦'
					},
					{
						image:'/static/dish/4.png',
						title:'鱼香肉丝',
						originalPrice:32,
						favourPrice:22,
						tip:'酸辣'
					},
					{
						image:'/static/dish/3.jpg',
						title:'老福山炸肉',
						originalPrice:32,
						favourPrice:22,
						tip:'不辣'
					},
				]
			}
		},
		onLoad() {
			this.load()
		},
		methods: {
			load() {
				uni.request({
					method: 'GET',
					url: 'http://192.168.2.246:3333/function',
					dataType: 'JSON',
					success: (res) => {
						this.data = res.data.data;
					}
				})
			}
		}
	}
</script>

<style>
	.state {
		color: #FFFFFF;
		height: 100%;
		background: #0077AA;
		text-align: center;
	}
</style>
