<template>
	<view>
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in data" :key="index">
				<view class="uni-media-list">
					<image class="uni-media-list-logo" :src="img"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.name}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.createdDate}}</view>
					</view>
					<view class="state">{{item.currentStateName}}</view>
				</view>
			</view>
			<load-more :loadText="loadText"></load-more>
		</view>
	</view>
</template>

<script>
	import loadMore from "../../components/common/load-more/load-more.vue"
	import uniLoadMore from "../../components/common/uni-load-more/uni-load-more.vue"

	export default {
		components: {
			loadMore,
			uniLoadMore
		},

		data() {
			return {
				pc: {
					pageIndex: 1,
					pageSize: 10
				},
				loadText: '上拉加载更多',
				img: '/static/dish/4.png',
				data: []
			}
		},
		onLoad() {
			this.load(1)
		},

		onPullDownRefresh() {
			console.log("onPullDownRefresh...")
			this.load(1)
			uni.hideNavigationBarLoading();
			uni.stopPullDownRefresh();
		},

		onReachBottom() {
			console.log("onReachBottom...")
			uni.showNavigationBarLoading();
			this.loadText = "加载中..."
			this.loadMore(this.pc.pageIndex + 1)
		},
		
		onNavigationBarSearchInputConfirmed(text) {
			console.log(text)
			this.load(1)
		},
		methods: {
			load(pageIndex) {
				uni.request({
					method: 'GET',
					url: 'http://192.168.2.246:3333/function?s=' + this.pc.pageSize + '&p=' + pageIndex,
					dataType: 'JSON',
					success: (res) => {
						let dataObj = JSON.parse(res.data)
						this.data = dataObj.data;
						this.pc = dataObj.pc;
					}
				})
			},

			loadMore(pageIndex) {
				if (this.pc.maxPages < pageIndex) {
					uni.showToast({
						title: '没有更多数据了',
						duration: 2000
					});
					this.loadText = '没有更多数据了'
					return
				}
				uni.request({
					method: 'GET',
					url: 'http://192.168.2.246:3333/function?s=' + this.pc.pageSize + '&p=' + pageIndex,
					dataType: 'JSON',
					success: (res) => {
						let dataObj = JSON.parse(res.data)
						this.data = this.data.concat(dataObj.data);
						this.pc = dataObj.pc;
						uni.hideNavigationBarLoading();
					}
				})
			}
		}
	}
</script>

<style>
.state {
	color: #0A98D5;
}
</style>
