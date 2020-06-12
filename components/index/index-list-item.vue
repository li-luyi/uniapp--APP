<template>
	<view class="index-list-item animated fadeInUp fast">
		<view class="user-info u-f-jsb">
			<view class="info u-f-ac">
				<image :src="item.userPic" mode="widthFix" lazy-load></image>
				{{item.userName}}
			</view>
			<view class="right-info u-f-ac">
				<view class="attention u-f-ac" v-if="!item.isGuanzhu" @tap="handleGuanzhu">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
				<view class="close-btn icon iconfont icon-guanbi"></view>
			</view>
		</view>
		<view class="title" @tap="openDetail">
			{{item.title}}
		</view>
		<view class="photo u-f-ajc" @tap="openDetail">
			<image :src="item.titlePic" mode="widthFix" lazy-load></image>
			<template v-if="item.type=='video'">
				<view class="playBtn icon iconfont icon-bofang"></view>
				<view class="play-info">
					<text>{{item.playNum}}</text> 次播放 <text>{{item.long}}</text>
				</view>
			</template>	
		</view>
		<view class="comment-toolbar u-f-jsb">
			<view class="left-tool u-f-ac">
				<view :class="{'active':item.infoNum.index==1}"><view class="icon iconfont icon-icon_xiaolian-mian" @tap="handleCaozuo('ding')"></view>{{item.infoNum.dingNum}}</view>
				<view :class="{'active':item.infoNum.index==2}"><view class="icon iconfont icon-kulian" @tap="handleCaozuo('cai')"></view>{{item.infoNum.caiNum}}</view>
			</view>
			<view class="right-tool u-f-ac">
				<view><view class="icon iconfont icon-pinglun1"></view>{{item.commentNum}}</view>
				<view><view class="icon iconfont icon-zhuanfa"></view>{{item.shareNum}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:{
				type:Object,
				default(){
					return null
				}
			}
		},
		data() {
			return {
				
			}
		},
		methods: {
			handleGuanzhu(){
				this.item.isGuanzhu=true
				uni.showToast({
					title:"关注成功",
					duration:1000
				})
			},
			handleCaozuo(type){
				let info=this.item.infoNum
				switch (type){
					case 'ding':
						if (info.index==1) {return}
						info.dingNum++
						if(info.index==2){
							info.caiNum--
						}
						info.index=1
						break;
					case 'cai':
						if (info.index==2) {return}
						info.caiNum++
						if(info.index==1){
							info.dingNum--
						}
						info.index=2
						break;
					default:
						break;
				}
			},
			openDetail(){
				console.log("进入详情页")
			}
		}
	}
</script>

<style lang="less" scoped>
		.index-list-item{
			border-bottom: 1px solid #efefef;
			padding: 20rpx;
			.user-info{
				color: #999999;
				.info{
					image{
						width: 100rpx;
						height: 100rpx;
						border-radius: 50%;
						margin-right: 20rpx;
					}
				}
				.right-info{
					.attention{
						background-color: #f4f4f4;
						color: #333;
						padding: 0 10rpx;
						border-radius: 2rpx;
						margin-right: 20rpx;
					}
				}
			}
			.title{
				color:#333;
				margin: 20rpx 0;
				font-weight: bold;
			}
			.photo>image{
				width: 100%;
				border-radius: 20rpx;
			}
			.photo{
				position: relative;
				color: #FFFFFF;
				.playBtn{
					position: absolute;
					font-size: 135rpx;
					
				}
				.play-info{
					position: absolute;
					right: 10rpx;
					bottom: 10rpx;
					background-color: rgba(0,0,0,.6);
					border-radius: 40rpx;
					padding: 5rpx 10rpx;
					line-height: 1.5;
					text{
						padding: 0 10rpx;
					}
				}
			}
			.comment-toolbar{
				color: #999999;
				.left-tool,.right-tool,.left-tool>view,.right-tool>view{
					.active{
						color: #ff9619;
					}
				}
				.left-tool>view,.right-tool>view:first-child{
					margin-right: 20rpx;
				}
				.left-tool>view>view,.right-tool>view>view{
					margin-right: 10rpx;
				}
			}
		}
		
</style>
