<template>
	<view class="content">
		<form action="" @submit="submitForm" @reset="resetForm">
			<view>
				<swiper checked @click="swiperChagee" name="swiperValue"></swiper>
			</view>
			<view>
				<radio-group name="selType">
					<label name="selType">
						<radio value="选项一"></radio><text>选项一</text>
					</label>
					<label name="selType">
						<radio value="选项二"></radio><text>选项一</text>
					</label>
					<label name="selType">
						<radio checked value="其他"></radio><text>其他选项</text>
					</label>
				</radio-group>
			</view>
			
			<view>
				<input class="uni-input" name="input" placeholder="这是一个输入框" />

			</view>
			
			<view>
				<textarea placeholder="请输入内容" name="textFinle"></textarea>
			</view>
			
			<view>
				<button  class="formBtn" form-type="submit">提交</button>
				<button  class="formBtn" form-type="reset">重置</button>
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			submitForm(e){
				console.log(e.detail),
				console.log(this.radio1),
				console.log(this.radio2)
			},
			resetForm(){
				console.log('清空数据')
			},
			swiperChagee(e){
				
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.formBtn{
		align-content: center;
		width: 200rpx;
		border-style: solid;
	}
		
	.uni-input{
		border-style: solid;
	}
</style>
