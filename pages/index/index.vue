<template>
	<view class="bg-white">
		<view class="cu-bar">
			<view class="action">
				<text class="cuIcon-title text-green"></text>
				<text>请选择你想要测算的内容</text>
			</view>
		</view>
		<view class="border-bottom pb-4">
			<view class="mb-3">
				<button class="cu-btn round mr-3" :class="calculationOptions==0?active:inactive" @tap="calculationOptions=0">最后想拥有的总资产</button>
				<button class="cu-btn round mr-3" :class="calculationOptions==1?active:inactive" @tap="calculationOptions=1">目标复合收益率</button>
			</view>
			<view>
				<button class="cu-btn round mr-3" :class="calculationOptions==2?active:inactive" @tap="calculationOptions=2">每期定投金额</button>
				<button class="cu-btn round mr-3" :class="calculationOptions==3?active:inactive" @tap="calculationOptions=3">定投总时长</button>
			</view>
		</view>
		
		<view v-if="calculationOptions!=2" class="cu-form-group">
			<view class="title">
				每期定投金额
			</view>
			<input placeholder="请输入" v-model="fixedMoney" type="digit"></input>
			<view class="action">
				<text>元</text>
			</view>
		</view>
		<view v-show="calculationOptions!=3" class="cu-form-group">
			<view class="title">
				总定投时长
			</view>
			<input placeholder="请输入" v-model="fixedTime" type="digit"></input>
			<view class="action">
				<text>年</text>
			</view>
		</view>
		<view class="cu-form-group">
			<view class="title">
				定投周期
			</view>
			<button class="cu-btn round mr-3" :class="period==0?active:inactive" @tap="period=0">周</button>
			<button class="cu-btn round mr-3" :class="period==1?active:inactive" @tap="period=1">两周</button>
			<button class="cu-btn round mr-3" :class="period==2?active:inactive" @tap="period=2">月</button>
		</view>
		<view v-show="calculationOptions!=1" class="cu-form-group">
			<view class="title">
				目标年复合收益率
			</view>
			<input placeholder="请输入" v-model="expectInterest" type="digit"></input>
			<view class="action">
				<text>%</text>
			</view>
		</view>
		<view v-show="calculationOptions!=0" class="cu-form-group">
			<view class="title">
				最后想拥有的总资产
			</view>
			<input placeholder="请输入" v-model="futureValue" type="digit"></input>
			<view class="action">
				<text>元</text>
			</view>
		</view>
		<view class="padding mt-5">
			<button class="weui-btn" type="primary" @tap="toResult">开始计算</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				calculationOptions: 0, //计算选项
				period: 2, //周期
				fixedMoney: '', //每期定投金额
				fixedTime: '', //定投时长
				expectInterest: '', //复合收益率
				futureValue: '', //终值
				active:'bg-green shadow-blur',//按钮活跃样式
				inactive:'line-gray shadow'//按钮不活跃样式
			}
		},
		methods: {
			/**
			 * 跳转计算结果页面
			 */
			toResult() {
				switch (this.calculationOptions) {
					case 0:
						if (this.fixedMoney == '') {
							uni.showToast({
								title: '请输入定投金额',
								icon: 'none'
							})
							return;
						} else if (this.fixedTime == '') {
							uni.showToast({
								title: '请输入定投时长',
								icon: 'none'
							})
							return;
						} else if (this.expectInterest == '') {
							uni.showToast({
								title: '请输入收益率',
								icon: 'none'
							})
							return;
						}
						break;
					case 1:
						if (this.fixedMoney == '') {
							uni.showToast({
								title: '请输入定投金额',
								icon: 'none'
							})
							return;
						} else if (this.fixedTime == '') {
							uni.showToast({
								title: '请输入定投时长',
								icon: 'none'
							})
							return;
						} else if (this.futureValue == '') {
							uni.showToast({
								title: '请输入想拥有的总资产',
								icon: 'none'
							})
							return;
						}
						break;
					case 2:
						if (this.expectInterest == '') {
							uni.showToast({
								title: '请输入收益率',
								icon: 'none'
							})
							return;
						} else if (this.fixedTime == '') {
							uni.showToast({
								title: '请输入定投时长',
								icon: 'none'
							})
							return;
						} else if (this.futureValue == '') {
							uni.showToast({
								title: '请输入想拥有的总资产',
								icon: 'none'
							})
							return;
						}
						break;
					case 3:
						if (this.fixedMoney == '') {
							uni.showToast({
								title: '请输入定投金额',
								icon: 'none'
							})
							return;
						} else if (this.expectInterest == '') {
							uni.showToast({
								title: '请输入收益率',
								icon: 'none'
							})
							return;
						} else if (this.futureValue == '') {
							uni.showToast({
								title: '请输入想拥有的总资产',
								icon: 'none'
							})
							return;
						}
						break;
					default:
						break;
				}
				//存储计算参数
				uni.setStorageSync('parameter', {
					option: this.calculationOptions,
					period: this.period,
					fixedMoney: this.fixedMoney, //每期定投金额
					fixedTime: this.fixedTime, //定投时长
					expectInterest: this.expectInterest, //复合收益率
					futureValue: this.futureValue, //终值
				});
				uni.navigateTo({
					url: '../result/result'
				})
			},
		}
	}
</script>

<style>
	/* 防止表单标题长短不一 */
	.cu-form-group .title {
		min-width: 300upx;
	}
</style>
