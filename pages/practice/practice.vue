<template>
	<view>
		<view>
			<!--每日一题顶部标题栏-->
			<view class="flex flex-wrap">
				<view class="flex-twice flex padding justify-start" @click="goBackToStudy">
					<text class="lg text-gray cuIcon-back"></text>
				</view>
				<view class="flex-twice flex padding">
					<text class="text-xl">每日一题</text>
				</view>
				<view class="flex-twice"></view>
			</view>
			<!--题型种类-->
			<view>
				<view class="flex padding justify-start">
					<view class="margin-xs margin-xs radius">
						<button class="cu-btn round line-blue">{{questionType}}</button>
					</view>
				</view>
			</view>
			<!--具体题目-->
			<view>
				<view class="padding-lg margin-lg nf-practice">
					<view class="flex flex-wrap justify-start">
						<text class="text-xl nf-bold-font">{{topicTitle}}</text>
					</view>
					<view>
						<!-- <image src="{{topicPicUrl}}"></image> -->
						<image src="../../static/pracice/topicPic1.jpg" mode="aspectFill"></image>
					</view>
					<view class="flex flex-wrap justify-start content-view" v-for="(item, index) in options" :key="index">
						<button class="cu-btn round line-black nf-border">{{item.serialNum}}</button>
						<text class="text-xl text-black nf-bold-font content-margin">{{item.content}}</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data() {
			return {
				questionType: '单选题',
				topicTitle: '以下程序执行后，角色面向的方向是 ( )',
				topicPicUrl: '../../static/practice/topicPic1.jpg',
				options: [
					{
						serialNum: 'A',
						content: '左上'
					},
					{
						serialNum: 'B',
						content: '左下'
					},
					{
						serialNum: 'C',
						content: '右上'
					},
					{
						serialNum: 'D',
						content: '右下'
					}
				]
			}
		},
		methods: {
			goBackToStudy() {
				// uni.navigateBack({
				// 	delta: 1
				// });
				uni.switchTab({
					url: '../study/study'
				});
				console.log('返回原来的页面');
			}
		},
		onLoad() {
			
		}
	}
</script>

<style>
	@import url("../../colorui/main.css");
	@import url("../../colorui/icon.css");
	
	.nf-practice {
		margin-top: 5rpx;
	}
	
	.content-view {
		margin-bottom: 10rpx;
	}
	.content-margin {
		margin-left: 10rpx;
	}
	
	.nf-border {
		border: 2rpx black solid;
		width: 50rpx;
		height: 50rpx;
		border-radius: 50%;
	}
</style>
