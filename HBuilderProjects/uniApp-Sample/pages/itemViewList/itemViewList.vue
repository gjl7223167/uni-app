<template>
	<view>
		<view @click="clickpop">弹窗</view>
		<view>
			<boxpop :state.sync="myState"></boxpop>
		</view>

		<view class="defclass" @click="clickMethod" :class="[curClass]"></view>

		<view class="nav">
			<view class="item" :class="navIndex==index ? 'active' : '' " @click="clickNav(index)"
				v-for="(item,index) in navtit">{{item.title}}</view>
		</view>

		<view>
			<view>{{year}}年{{month}}月{{day}}日</view>
			<picker-view v-if="visible" :indicator-style="indicatorStyle" :value="value" @change="bindChange"
				class="picker-view">
				<picker-view-column>
					<view class="item" v-for="(item,index) in years" :key="index">{{item}}年</view>
				</picker-view-column>
				<picker-view-column>
					<view class="item" v-for="(item,index) in months" :key="index">{{item}}月</view>
				</picker-view-column>
				<picker-view-column>
					<view class="item" v-for="(item,index) in days" :key="index">{{item}}日</view>
				</picker-view-column>
			</picker-view>
		</view>
		
		<view class="computedType">
			<input class="inputItem" v-model="computedValue1" />
			<input class="inputItem" v-model="computedValue2" />
			<label>{{inpudSum}}</label>
		</view>
		
		<button @click="onPageValue">大标题</button>
		<pageTitleComponents :title.sync="pageValue" :subtitle.sync="pageValuetwo"></pageTitleComponents>
		
	</view>
</template>

<script>
	export default {
		data() {
			// pickview 相关数据
			const date = new Date()
			const years = []
			const year = date.getFullYear()
			const months = []
			const month = date.getMonth() + 1
			const days = []
			const day = date.getDate()
			for (let i = 1990; i <= date.getFullYear(); i++) {
				years.push(i)
			}
			for (let i = 1; i <= 12; i++) {
				months.push(i)
			}
			for (let i = 1; i <= 31; i++) {
				days.push(i)
			}
			return {
				// pickview 相关数据
				years,
				year,
				months,
				month,
				days,
				day,
				// value: [10, month - 1, day - 1],
				value: [32, month - 1, day - 1],
				visible: true,
				indicatorStyle: `height: 50px;`,

				// 动态class相关数据
				myState: false,
				curClass: '',
				curNumber: 0,
				navtit: [{
						id: 1,
						title: "列1"
					},
					{
						id: 2,
						title: "列2"
					},
					{
						id: 3,
						title: "列3"
					},
					{
						id: 4,
						title: "列4"
					}
				],
				navIndex: 0,
				
				//inputed相关
				computedValue1:"",
				computedValue2:"",
				
				//响应式
				pageValue:"",
				pageValuetwo:""
			};
		},
		methods: {
			clickpop() {
				this.myState = true
			},
			clickMethod() {

				console.log('....' + this.curNumber)
				if (this.curNumber == 0) {
					this.curClass = 'defclass'
				} else if (this.curNumber == 1) {
					this.curClass = 'aclass'
				} else if (this.curNumber == 2) {
					this.curClass = 'bclass'
				} else {
					this.curClass = 'dclass'
					this.curNumber = 0
				}

			},
			clickNav(e) {
				this.navIndex = e
				console.log(e)
			},
			bindChange(e) {
				const val = e.detail.value
				console.log(val)
				this.year = this.years[val[0]]
				this.month = this.months[val[1]]
				this.day = this.days[val[2]]
			},
			onPageValue(){
				console.log("大标题")
				this.pageValue="大标题"
				this.pageValuetwo="介绍一下"
			}
		},
		computed:{
			inpudSum(){
				let sum = parseInt(this.computedValue1) + parseInt(this.computedValue2)
				console.log(sum)
				return "合并后" + (isNaN(sum) ? 0 : sum)
			},
	
		}
	}
</script>

<style lang="scss">
	.defclass {
		width: 100rpx;
		height: 100rpx;
		background: gray;
	}

	.aclass {
		width: 200rpx;
		height: 200rpx;
		background: pink;
	}

	.bclass {
		width: 300rpx;
		height: 300rpx;
		background: pink;
	}

	.dclass {
		width: 400rpx;
		height: 400rpx;
		background: pink;
	}

	.nav {
		display: flex;
		justify-content: space-around;
		align-items: center;

		.item {
			flex: 1;
			text-align: center;
			line-height: 99rpx;
			background: #ccc;

			&.active {
				background: #009a33;
			}
		}
	}

	.picker-view {
		width: 750rpx;
		height: 600rpx;
		margin-top: 20rpx;
		background: #009a33;

		.item {
			line-height: 100rpx;
			text-align: center;
		}
	}
	.computedType{
		display: flex;
		flex-direction: column;
		margin: 10rpx 10rpx;
		background: #ccc;
		.inputItem{
			margin: 10rpx 10rpx;
			min-height: 50rpx;
			background: #fff;
			border:1prx solid;
			border-radius: 5rpx;
		}
	}
</style>