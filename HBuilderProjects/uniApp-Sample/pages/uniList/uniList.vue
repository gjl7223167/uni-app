<template>
	<view>
		<boxItem v-bind:bottomImgCount="numValye(imgCount)" v-bind:topImgCount="3" @boxImageTag="boxClickIndex">
		</boxItem>
		<view class="box">
			<input type="number" v-model.number="imgCount" placeholder="请输入图片数量" />
		</view>
		{{imgCount}}

	</view>


</template>

<script>
	export default {
		data() {
			return {
				imgCount: 0
			};
		},
		methods: {
			numValye() {
				return Number(this.imgCount)
			},
			boxClickIndex(e) {
				uni.showToast({
					title: String("这是第"+e+"张图"),
					image:"../../static/toash.png",
					duration: 850
				})
				uni.navigateTo({
					// url:"/pages/imgDetail/imgDetail?path=../../static/monv-3.jpeg"
				})
			}
		}
	}
</script>

<style lang="scss">
	input {
		font-size: 35rpx;
	}

	.box {
		margin: 20rpx;
		border: 1rpx solid #ccc;
	}
</style>