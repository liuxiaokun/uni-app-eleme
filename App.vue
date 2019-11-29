<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>
<style>
	/*每个页面公共css */
	@import './common/uni.css';
	
	/*引入阿里巴巴自定义图标库*/
	@import './common/icon/iconfont.css';
	
	/*引入动画库库*/
	@import './common/animate.css';
</style>
