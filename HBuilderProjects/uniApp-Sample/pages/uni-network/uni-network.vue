<template>
	<view class="out">
		<view class="row" @click="toDetails">
			<view class="content">
				{{inspire.content}}
			</view>
			<view class="author">{{'作者:'+inspire.source}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// myRequestUrl: "https://api.qqsuu.cn/api/dm-xjj",
				myRequestUrl: "https://api.qqsuu.cn/api/dm-pyqwenan",
				inspire:{},
				detailsInfo:{'a':'b','c':'d','e':'f'}
			};
		},
		methods: {
			toDetails() {
				console.log(encodeURIComponent(JSON.stringify(this.detailsInfo)));
					const des = encodeURIComponent(JSON.stringify(this.detailsInfo));

				uni.navigateTo({
					url:`/pages/netWorkDetails/netWorkDetails?id=${des}`
				}) 
			}
		},
		onLoad() {
			
		},
		onShow() {
			console.log(this.myRequestUrl);
			let that = this;
			uni.showLoading({
				title:'数据加载中......',
				mask:true,
			})
			uni.request({
				url: that.myRequestUrl,
				method:"GET",
				dataType: "JSON",
				success: (res) => {					
					that.inspire = res.data.data
				},
				complete() {
					uni.hideLoading()
				}
			})
		}
	}
</script>

<style lang="scss">
.out{
	padding: 50rpx 30rpx;
	.row{
		padding: 20rpx 10rpx;
		border-bottom: 1rpx dotted #656bcb;
		.content{
			color: #888;
			font-size: 36rpx;
		}
		.author{
			color: #000;
			font-size: 40rpx;
			text-align: right;
		}
	}
}
</style>