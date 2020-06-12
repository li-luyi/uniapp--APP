<template>
	<view>
		搜索页
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		// 监听原生标题按钮点击事件
		onNavigationBarButtonTap(e){
			if (e.index==0) {
				uni.navigateBack({
					delta:1
				})
			}
		},
		// 监听搜索框内容变化
		onNavigationBarSearchInputChanged(e){
			console.log(e,11)
		},
		// 点击软键盘搜索触发事件
		onNavigationBarSearchInputConfirmed(e){
			console.log(e,22)
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
