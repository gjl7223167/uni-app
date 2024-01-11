<template>
	<view class="content">
		<form action="" @submit="submitForm" @reset="resetForm">
			<view class="uni-list">
				<view class="uni-list-cell-pd uni-list-cell">
					<view class="uni-list-cell-db">开启中</view>
					<switch checked @click="swiperChagee" name="swiperValue"></switch>
				</view>
			</view>
			<view class="row">
				<radio-group name="selType" class="v-radio">
					<label name="selType" class="v-row">
						<radio value="选项一id"></radio><text>选项一</text>
					</label>
					<label name="selType" class="v-row">
						<radio value="选项二id"></radio><text>选项一</text>
					</label>
					<label name="selType" class="v-row">
						<radio checked value="其他id"></radio><text>其他选项</text>
					</label>
				</radio-group>
			</view>
			<view>
				<picker :range="options" mode="multiSelector" name="school" :value="selectValue" @change="pickChange">
					<label class="barder_row">点击请选择学历:{{options[selectValue]}}</label>
				</picker>
			</view>

			<view class="table_row">
				<input class="uni-input" name="input" placeholder="请输入" />
			</view>

			<view>
				<textarea placeholder="请输入内容" name="textFinle"></textarea>
			</view>


			<view>
				<button class="formBtn" form-type="submit">提交</button>
				<button class="formBtn" form-type="reset">重置</button>
			</view>
			{{obj}}
		</form>
	
	<input type="text" v-model="title" />
	<view>原标题: {{title}}</view>
	<view>修改后: {{changeTitle}}</view>
	
	<view>{{demo}}</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				obj: null,
				options: ["大专", "本科", "研究生", "博士"],
				selectValue: 2,
				
				title : "",
				text: "你是谁"
			}
		},
		onLoad() {

		},
		computed:{
			demo(){
				return "uniapp" + this.text
			},
			changeTitle(){
			 	return this.title.toLocaleUpperCase()
			}
		},

		methods: {
			submitForm(e) {
				console.log(e.detail)
				this.obj = e.detail.value
				this.obj.school = this.options[this.selectValue]
			},
			resetForm() {
				console.log('清空数据')
			},
			swiperChagee(e) {

			},
			pickChange(e) {
				this.selectValue = e.detail.value
			}
		}
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		margin: 10px;
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

	.formBtn {
		align-content: center;
		width: 200rpx;
		border-style: solid;
	}

	.table_row {
		margin-top: 10px;
		padding: 6px;
	}

	input,
	textarea {
		border: solid 1px #ccc;
		margin-top: 10px;
		border-radius: 5px;
		padding: 6px;
	}

	.barder_row {
		border: solid 2px #ccc;
		border-radius: 5px;
		background-color: #8f8f94;
		padding: 6px;
	}

	.row {
		margin-bottom: 10px;

		.v-radio {
			display: grid;
			margin-bottom: 10rpx;

			.v-row {
				margin-bottom: 10px;
			}
		}
	}

	.uni-list {
		display: flex;
		flex-direction: column;
		position: relative;
	}

	.uni-list-cell-db {
		flex: 1;
	}

	.uni-list-cell {
		position: relative;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	
	.uni-list-cell-pd {
		padding: 22rpx 30rpx;
	}

	.uni-list-cell::after {
		display: flex;
		position: absolute;
		z-index: 3;
		right: 0;
		bottom: 0;
		left: 30rpx;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}
</style>