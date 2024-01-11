<template>
	<view class="pubTitle">
		<view class="big" @click="toClick">{{title}}</view>
		<view class="small">{{subtitle}}</view>
		<view>{{list}}</view>
		<view>{{user}}</view>
		<view class="line"></view>
	</view>
</template>

<script>
	export default {
		name:"pageTitleComponents",
		props:{
			title:{
				type:String,
				default:"一个标题"
			},
			subtitle:{
				type:String, 
				default:"副标题"
			},
			list:{
				type:Array,
				default(){
					return [1,2,3]
				}
			},
			user:{
				type:Object,
				default(){
					return {name:"五六",gander:"未知"}
				}
			},
			
		},
		methods:{
			toClick(){
				this.$emit("update:title","小标题")
				this.$emit("update:subtitle","副标题")
				
				console.log(this.title + this.subtitle)
			}
		},
		data() {
			return {
				
			};
		},
	}
	
</script>

<style lang="scss">

.pubTitle{
	background: #888;
	margin: 10rpx 30rpx;
	text-align:center;	
	.big{
		font-size: 50rpx;
		font-weight: 600;
		color: #222;
	}
	.small{
		 font-size: 29rpx;
		 color: #333;
	}
	.line{
		display: inline-block; 
		width: 80rpx;
		height: 8rpx;
		background: #1aa034;
		border-radius: 10rpx;
		margin-bottom: 2rpx;
		margin-top: 50rpx;
	}
}


</style>