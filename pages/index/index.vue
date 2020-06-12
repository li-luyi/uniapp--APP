<template>
	<view>
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" @change="tabChange" :current="tabIndex">
				<swiper-item v-for="(item,index) in newsList" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="handlLoadMore(index)">
						<template v-if="item.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(it,i) in item.list" :key="i">
								<index-list-item :item="it"></index-list-item>
							</block>
							<!-- 上拉加载 -->
							<load-more :loadText="item.loadText"></load-more>
						</template>
						<!-- 无内容默认展示 -->
						<template v-if="item.list.length==0">
							<no-ting></no-ting>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import indexListItem from "../../components/index/index-list-item.vue"
	import swiperTabHead from "../../components/index/swiper-tab-head.vue"
	import loadMore from "../../components/common/load-more.vue"
	import noTing from "../../components/common/no-ting.vue"
	export default {
		data() {
			return {
				swiperHeight:0,
				tabIndex: 0,
				tabBars: [{
					name: '关注',
					id: 'guanzhu'
				}, {
					name: '推荐',
					id: 'tuijian'
				}, {
					name: '体育',
					id: 'tiyu'
				}, {
					name: '热点',
					id: 'redian'
				}, {
					name: '财经',
					id: 'caijing'
				}, {
					name: '娱乐',
					id: 'yule'
				}, {
					name: '军事',
					id: 'junshi'
				}, {
					name: '历史',
					id: 'lishi'
				}, {
					name: '本地',
					id: 'bendi'
				}],
				newsList: [
				{
					loadText:"上拉加载更多",
					list: [{
							userPic: "../../static/image/userpic/10.jpg",
							userName: "李小仙",
							isGuanzhu: false,
							title: "如何用手账改变你的一生？",
							type: "img", //img:图片，video：视频
							titlePic: "../../static/image/datapic/11.jpg",
							playNum: "20w",
							long: "2:37",
							infoNum: {
								index: 0, //0:没有进行顶踩操作，1：反之
								dingNum: 22,
								caiNum: 381
							},
							commentNum: 1340,
							shareNum: 10
						},
						{
							userPic: "../../static/image/userpic/10.jpg",
							userName: "李da仙",
							isGuanzhu: true,
							title: "如何用手账改变你的一生？",
							type: "video",
							titlePic: "../../static/image/datapic/11.jpg",
							playNum: "21w",
							long: "2:37",
							infoNum: {
								index: 0, //0:没有进行顶踩操作，1：顶操作；2：踩操作
								dingNum: 233,
								caiNum: 38
							},
							commentNum: 100,
							shareNum: 10
						}
					]
				},{
					loadText:"上拉加载更多",
					list:[
						{
								userPic: "../../static/image/userpic/10.jpg",
								userName: "李小仙",
								isGuanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", //img:图片，video：视频
								titlePic: "../../static/image/datapic/11.jpg",
								playNum: "20w",
								long: "2:37",
								infoNum: {
									index: 0, //0:没有进行顶踩操作，1：反之
									dingNum: 22,
									caiNum: 381
								},
								commentNum: 1340,
								shareNum: 10
							},
							{
								userPic: "../../static/image/userpic/10.jpg",
								userName: "李da仙",
								isGuanzhu: true,
								title: "如何用手账改变你的一生？",
								type: "video",
								titlePic: "../../static/image/datapic/11.jpg",
								playNum: "21w",
								long: "2:37",
								infoNum: {
									index: 0, //0:没有进行顶踩操作，1：反之
									dingNum: 233,
									caiNum: 38
								},
								commentNum: 100,
								shareNum: 10
							},
							{
									userPic: "../../static/image/userpic/10.jpg",
									userName: "李小仙",
									isGuanzhu: false,
									title: "如何用手账改变你的一生？",
									type: "img", //img:图片，video：视频
									titlePic: "../../static/image/datapic/11.jpg",
									playNum: "20w",
									long: "2:37",
									infoNum: {
										index: 0, //0:没有进行顶踩操作，1：反之
										dingNum: 22,
										caiNum: 381
									},
									commentNum: 1340,
									shareNum: 10
								},
								{
									userPic: "../../static/image/userpic/10.jpg",
									userName: "李da仙",
									isGuanzhu: true,
									title: "如何用手账改变你的一生？",
									type: "video",
									titlePic: "../../static/image/datapic/11.jpg",
									playNum: "21w",
									long: "2:37",
									infoNum: {
										index: 0, //0:没有进行顶踩操作，1：反之
										dingNum: 233,
										caiNum: 38
									},
									commentNum: 100,
									shareNum: 10
								}
					]
				},
				{
					list:[
						{
								userPic: "../../static/image/userpic/10.jpg",
								userName: "李小仙",
								isGuanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", //img:图片，video：视频
								titlePic: "../../static/image/datapic/11.jpg",
								playNum: "20w",
								long: "2:37",
								infoNum: {
									index: 0, //0:没有进行顶踩操作，1：反之
									dingNum: 22,
									caiNum: 381
								},
								commentNum: 1340,
								shareNum: 10
							},
							{
								userPic: "../../static/image/userpic/10.jpg",
								userName: "李da仙",
								isGuanzhu: true,
								title: "如何用手账改变你的一生？",
								type: "video",
								titlePic: "../../static/image/datapic/11.jpg",
								playNum: "21w",
								long: "2:37",
								infoNum: {
									index: 2, //0:没有进行顶踩操作，1：反之
									dingNum: 233,
									caiNum: 38
								},
								commentNum: 100,
								shareNum: 10
							},
							{
									userPic: "../../static/image/userpic/10.jpg",
									userName: "李小仙",
									isGuanzhu: false,
									title: "如何用手账改变你的一生？",
									type: "img", //img:图片，video：视频
									titlePic: "../../static/image/datapic/11.jpg",
									playNum: "20w",
									long: "2:37",
									infoNum: {
										index: 0, //0:没有进行顶踩操作，1：反之
										dingNum: 22,
										caiNum: 381
									},
									commentNum: 1340,
									shareNum: 10
								},
								{
									userPic: "../../static/image/userpic/10.jpg",
									userName: "李da仙",
									isGuanzhu: true,
									title: "如何用手账改变你的一生？",
									type: "video",
									titlePic: "../../static/image/datapic/11.jpg",
									playNum: "21w",
									long: "2:37",
									infoNum: {
										index: 0, //0:没有进行顶踩操作，1：反之
										dingNum: 233,
										caiNum: 38
									},
									commentNum: 100,
									shareNum: 10
								},
								{
										userPic: "../../static/image/userpic/10.jpg",
										userName: "李小仙",
										isGuanzhu: false,
										title: "如何用手账改变你的一生？",
										type: "img", //img:图片，video：视频
										titlePic: "../../static/image/datapic/11.jpg",
										playNum: "20w",
										long: "2:37",
										infoNum: {
											index: 0, //0:没有进行顶踩操作，1：反之
											dingNum: 22,
											caiNum: 381
										},
										commentNum: 1340,
										shareNum: 10
									},
									{
										userPic: "../../static/image/userpic/10.jpg",
										userName: "李da仙",
										isGuanzhu: true,
										title: "如何用手账改变你的一生？",
										type: "video",
										titlePic: "../../static/image/datapic/11.jpg",
										playNum: "21w",
										long: "2:37",
										infoNum: {
											index: 0, //0:没有进行顶踩操作，1：反之
											dingNum: 233,
											caiNum: 38
										},
										commentNum: 100,
										shareNum: 10
									}
					]
				},
				{
					loadText:"上拉加载更多",
					list:[]
				},
				{
					loadText:"上拉加载更多",
					list:[]
				}
				]
			}
		},
		components: {
			indexListItem,
			swiperTabHead,
			loadMore,
			noTing
		},
		onLoad() {
			let _this=this
			uni.getSystemInfo({
			    success: function (res) {
					_this.swiperHeight=res.windowHeight-uni.upx2px(102)
			    }
			});
		},
		// 监听原生标题按钮点击事件
		onNavigationBarButtonTap(e){
			switch (e.index){
				case 1:
					// 打开发布页
					uni.navigateTo({
						url:"../app-input/app-input"
					})
					break;
				case 0:
					// 打开发布页
					break;	
				default:
					break;
			}
		},
		onNavigationBarSearchInputClicked(){
			// 跳转搜索页
			uni.navigateTo({
				url:"../search/search"
			})
		},
		methods: {
			tabtap(index){
				this.tabIndex=index
			},
			tabChange(e){
				this.tabIndex=e.detail.current
			},
			handlLoadMore(index){
				if (this.newsList[index].loadText!="上拉加载更多") {
					return;
				}else{
					this.newsList[index].loadText="加载中..."
					let timeId=setTimeout(()=> {
						let obj={
									userPic: "../../static/image/userpic/10.jpg",
									userName: "傻儿",
									isGuanzhu: false,
									title: "如何用手账改变你的一生？",
									type: "img", //img:图片，video：视频
									titlePic: "../../static/image/datapic/11.jpg",
									playNum: "20w",
									long: "2:37",
									infoNum: {
										index: 0, //0:没有进行顶踩操作，1：反之
										dingNum: 22,
										caiNum: 381
									},
									commentNum: 1340,
									shareNum: 10
								}
						this.newsList[index].list.push(obj)
						this.newsList[index].loadText="上拉加载更多"
					},1000)
				}
			}
		}
	}
</script>

<style lang="less" scoped>

</style>