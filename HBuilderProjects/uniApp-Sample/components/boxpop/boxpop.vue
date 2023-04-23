<template>
	<view>
		<view>弹出框</view>
		<view class="xbox" :style="{height:state?'300rpx':'0'}">
			<label style="{overflow:hidden}">正在差量编译......</label>
		</view>
		<button size="mini" @click="clickBtn">关闭</button>
	</view>
</template>

<script>
	export default {
		name:"boxpop",
		data() {
			return {
				
			};
			
		},
		props:{
			state:{
				type:Boolean,
				default: false
			}
		},
		methods: {
			clickBtn() {
 				this.$emit("update:state",false)
			}
		}
		
	}
</script>

<style lang="scss">
	.xbox{
		height: 300rpx;
		width: 300rpx;
		background-color: pink;
		overflow: hidden;
	}
</style>