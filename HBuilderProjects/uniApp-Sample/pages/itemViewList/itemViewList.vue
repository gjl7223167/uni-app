<template>
	<view>
		<view @click="clickpop">弹窗</view>
		<view>
			<boxpop :state.sync="myState"></boxpop>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				myState:false
			};
		},
		methods: {
			clickpop() {
				this.myState = true
			},
		}
	}
</script>

<style lang="scss">

</style>