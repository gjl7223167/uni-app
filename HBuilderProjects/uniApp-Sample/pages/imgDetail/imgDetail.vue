<template>
	<view>
		<view type="{height:500rpx;width:750rpx}">
			<image mode="aspectFill" :src="imgPath" ></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgPath: ''
			};
		},

		onLoad(e) {
			this.imgPath = e.path,
			console.log(this.imgPath)
		}
	}
</script>

<style lang="scss">

</style>