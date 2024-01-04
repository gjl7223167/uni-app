<template>
	<view>
		<!-- ${} 拼接变量方式-->
		{{`这个是详情${this.txtid}`}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				txtid: '123'
			};
		},

		methods: {

		},

		onLoad(option) {
			const item = JSON.parse(decodeURIComponent(option.id));
			console.log('传值是多少',item);
		},
	}
</script>

<style lang="scss" scoped>

</style>