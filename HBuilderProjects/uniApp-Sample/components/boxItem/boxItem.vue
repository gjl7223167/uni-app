<template>
	<view>
		<scroll-view scroll-x="true" class="scrollItem">
			<view class="group">
				<image class="item" src="../../static/monv-3.jpeg" mode="aspectFill"  v-for="(item,index) in this.topImgCount" :key="index"></image>
			</view>
			
		</scroll-view>
		
		<swiper autoplay="ture" circular="ture" interval="1500" indicator-dots indicator-color="#ccc" indicator-active-color="#f6f " class="swiperbox">
			<swiper-item v-for="(item,index) in this.bottomImgCount" :key="index" @click="clickImage(index)">
				<image class="item" src="../../static/monv-3.jpeg" mode="aspectFill"></image>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		name:"boxItem",
		props:{
			topImgCount:{
				type: Number,
				default: 3
			},
			bottomImgCount:{
				type: Number,
				default: 3
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			clickImage(e){
				this.$emit("boxImageTag",e);
			}
		}
	}
</script>

<style lang="scss">

.scrollItem{
	width: 760rpx;
	height: 500rpx;
	background-color: #4df;
	.group{
		white-space: nowrap;
		.item{
			display: inline-block;
			height: 500rpx;
			width: 760rpx;
			margin-right: 10rpx;
		} 
	}
}
.swiperbox{
	margin-top:20rpx;
	width: 760rpx;
	height: 500rpx;
	.item{
		display: inline-block;
		height: 500rpx;
		width: 760rpx;
		margin-right: 10rpx;
	}
}
</style>