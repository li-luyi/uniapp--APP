<template>
	<view class="load-more">{{loadText}}</view>
</template>

<script>
	export default{
		props:{
			loadText:{
				type:String
			}
		},
	}
</script>
<style lang="less" scoped>
	.load-more{
		text-align: center;
		color: #aaa;
		padding: 10rpx;
	}
</style>
