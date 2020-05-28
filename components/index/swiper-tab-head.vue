<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" :class="{active:tabIndex==index}" @tap="tabtap(index)">
					{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars:{
				type:Array,
				default(){
					return []
				}
			},
			tabIndex:{
				type:Number,
				default:0
			}
		},
		data() {
			return {
				
			}
		},
		methods: {
			tabtap(index) {
				this.$emit("tabtap",index)
			},
		}
	}
</script>

<style lang="less" scoped>
	.swiper-tab-list {
		font-weight: bold;
		color: #969696;
	}

	.uni-tab-bar .active {
		color: #343434;

		.swiper-tab-line {
			border-bottom: 10upx solid #fede33;
			width: 70upx;
			margin: auto;
			border-radius: 10upx;
		}
	}

	.uni-swiper-tab {
		border-bottom: 1px solid #EEEEEE;
	}
</style>