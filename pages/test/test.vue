<template>
	<view>
		<!-- <view class="icon iconfont icon-icon-test4 animated fadeOutDown" style="color: #09BB07; font-size: 100px;"></view>
		<uni-badge text="1"></uni-badge>
		<uni-badge text="2" type="success" @click="bindClick"></uni-badge>
		<uni-badge text="3" type="primary" :inverted="true"></uni-badge> -->
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in functionData" :key="index">
				<view class="uni-media-list">
					<image class="uni-media-list-logo" :src="item.img"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.name}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.createdDate}}</view>
					</view>
				</view>
			</view>
		</view>
		<uni-drawer :visible="visible" :mode="direct" :mask="true">
		    <uni-list>
				<block v-for="(item, index) in projectData" :key="index">
					<uni-list-item :title="item.name" :shLow-arrow="false" :show-badge="true" badge-text="12" @click="queryFuction(item.id)"></uni-list-item>
				</block>
		    </uni-list>
		</uni-drawer>
	</view>
</template>

<script>
import { uniBadge, uniDrawer, uniList, uniListItem } from '@dcloudio/uni-ui';

export default {
	components: {
		uniBadge,
		uniDrawer,
		uniList,
		uniListItem
	},
	data() {
		return {
			visible: true,
			direct: 'right',
			pc:{
				pageIndex:1,
				pageSize:10
			},
			projectData:[],
			functionData:[]
		};
	},
	onLoad() {
		this.load(1)
	},
	methods: {
		bindClick() {
			console.log(111);
		},
		change() {
			console.log(change);
		},
		load(pageIndex) {
			uni.request({
				method: 'GET',
				url: 'http://192.168.2.246:3333/project',
				dataType: 'JSON',
				success: (res) => {
					this.projectData = res.data.data;
				}
			})
		},
		queryFuction(id) {
			console.log(id)
			this.visible = false;
			uni.request({
				method: 'GET',
				url: 'http://192.168.2.246:3333/function?s=' + this.pc.pageSize + '&p=' + this.pc.pageIndex + '&projectId=' + id,
				dataType: 'JSON',
				success: (res) => {
					this.functionData = res.data.data;
					this.pc = res.data.pc;
				}
			})
		}
	}
};
</script>

<style></style>
