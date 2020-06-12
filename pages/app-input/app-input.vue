<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar left-icon="arrowleft" @clickLeft="back" :statusBar="true" right-text="发布" @clickRight="submit">
			<!-- 插槽 -->
			<view class="u-f-ajc slot-navbar-title" @tap="changeLookType">
				{{lookType}}<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	export default {
		data() {
			return {
				lookType:"所有人可见"
			}
		},
		components:{
			uniNavBar
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			submit(){},
			changeLookType(){
				let changlooks=['所有人可见', '仅自己可见']
				uni.showActionSheet({
				    itemList: changlooks,
				    success: (res) =>{
						this.lookType=changlooks[res.tapIndex]
				    }
				});
			}
		}
	}
</script>

<style lang="less" scoped>
	.slot-navbar-title{
		width: 100%;
	}
</style>
