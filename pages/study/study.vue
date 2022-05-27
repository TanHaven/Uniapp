<template>
	<view>
		<scroll-view scroll-x class="nav text-center">
			<view class="cu-item" :class="index==TabCur?'text-blue cur':''" v-for="(item,index) in titles" :key="index" @tap="tabSelect" :data-id="index">
				<text class="text-xl"  @click="checked(index)">{{item}}</text>
			</view>
		</scroll-view>
		<!--题库板块--> 
		<view v-if="this.currentIndex == 0" class="nav-item">
			<!--每日一题板块-->
			<view @click="goToPractice">
				<view class="bg-white padding-lg margin-lg radius shadow-lg shadow nf-border">
					<view class="flex flex-wrap bg-white justify-start">
						<text class="text-xl nf-bold-font">每日一题</text>
					</view>
					<view class="flex flex-wrap bg-white justify-between basis-xs">
						<view class="bg-white">
							<text class="bg-white text-xs">A Daily Topic</text>	
						</view>
						<view>
							<image class="nf-image" src="../../static/study/dailyTopicPic.jpg"></image>
						</view>
					</view>
					<!--解决方法二：-->
					<!-- <view class="bg-white padding-lg margin-lg radius shadow-lg shadow nf-border"> -->
						<!-- <view class="flex flex-wrap bg-white justify-start"> -->
						<!-- 	<text class="text-xl nf-bold-font">每日一题</text> -->
						<!-- </view> -->
						<!-- <view class="flex flex-wrap bg-white justify-start basis-xs"> -->
							<!-- <text class="text-xs">A Daily Topic</text> -->
						<!-- </view> -->
						<!-- <view class="flex bg-blue justify-end"> -->
							<!-- <image class="nf-image" src="../../static/study/dailyTopicPic.jpg"></image> -->
					<!-- 	</view> -->
					<!-- </view> -->
				</view>
			</view>
			<!--题目总内容板块-->
			<view>
				<view class="flex flex-wrap">
					<view class="flex solid-bottom padding justify-start">
						<!--题目左边的蓝色区域-->
						<view class="bg-blue margin-xs margin-xs radius nf-left-rectangle"></view>
						<!--题目右边边的文字区域-->
						<view class="margin-sm nf-margin-sm radius">
							<text class="text-xl nf-bold-font">题目库</text>
						</view>
					</view>
			</view>
			<!--题目选择的列表-->
				<view class="flex bg-white padding-lg margin-sm radius shadow nf-border justify-between nf-topic-height" v-for="(item, index) in topicList" :key="index">
					<!--题目文字板块-->
					<view class="bg-white">
						<view class="bg-white">
							<text class="text-lg nf-bold-font">{{item.tittle}}</text>
						</view>
						<view class="bg-white">
							<text class="text-df">{{item.totalCount | showTotalCount(item.totalCount)}}</text>
						</view>
					</view>
					<!--题目按钮板块-->
					<view class="bg-white">
						<button class="cu-btn round bg-green" @click="goToPractice">练习</button>
					</view>
				</view>
		
			</view>
		</view>
		<!--课堂板块-->
		<view v-if="this.currentIndex == 1"  class="nav-item">
			<text>课堂板块</text>
		</view>	
		<!--智慧树板块-->
		<view v-if="this.currentIndex == 2"  class="nav-item">
			<text>智慧树板块</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabCur: 0,
				titles: ['题库', '课堂', '智慧树'],
				currentIndex: 0 ,// 关于顶部tab的对应内容跳转
				topicList: [
					{
						tittle: 'Python总题库',
						totalCount: 336
					},
					{
						tittle: 'Scratch总题库',
						totalCount: 221
					},
					{
						tittle: 'C语言总题库',
						totalCount: 401
					}
				]
			}
		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			checked(index) {
				this.currentIndex = index;
				console.log('index = ' + index);
			},
			goToPractice() {
				uni.navigateTo({
					url: '../practice/practice'
				})
				console.log('点击到了习题的跳转页面。。');
			}
			
		},
		filters: {
			showTotalCount(price) {
				return price + '题';
			}
		}
	}
</script>

<style>
	@import url("../../colorui/main.css");
	
	view{
		background-color: #EEEEEE;
	}
	
	.nf-bold-font{
		font-weight: bold;
	}
	
	.nf-border{
		border-radius: 25rpx;
	}
	
	.nf-image{
		width: 300rpx;
		height: 250rpx;
	}
	
	.nf-left-rectangle{
		width: 30rpx;
		height: 65rpx;
		border-radius: 30rpx;
	}
	
	.nf-margin-sm{
		margin-left: 5rpx;
		margin-top: 14rpx;
	}
	
	.nf-topic-height{
		height: 150rpx;
	}
</style>
