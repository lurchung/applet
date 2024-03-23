<template>
	<view class="applet">
		<view class="top">
			<view class="left">
				3月20日 周三
			</view>
			<view class="right">
				农历二月十一
			</view>
		</view>
		<view class="group">
			<view :class="currentindex==index? 'group-1 active' : 'group-1'" v-for="(item,index) in array1"
				@click="active(index)" :key="index">
				<view class="top">
					<view class="left">
						{{item.date}} {{item.week}}
					</view>
					<view class="right">
						{{item.ldate}}
					</view>
				</view>
				<view class="main">
					<view class="txt">
						{{item.txt}}
					</view>
					<view class="time">
						<text class="start">20:00</text>
						<text class="end">20:30</text>
					</view>
				</view>
			</view>
		</view>
		<view class="new">
			<navigator url="/pages/new-schedule/new-schedule">+</navigator>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				array1: [{
						date: '3月21日',
						ldate: '农历二月十二',
						week: '周四',
						txt: '涨知识时间到！快来百度翻译...',
					},
					{
						date: '3月22日',
						ldate: '农历二月十三',
						week: '周五',
						txt: '涨知识时间到！快来百度翻译...',
					},
					{
						date: '3月23日',
						ldate: '农历二月十四',
						week: '周六',
						txt: '涨知识时间到！快来百度翻译...',
					},
					{
						date: '3月24日',
						ldate: '农历二月十五',
						week: '周日',
						txt: '涨知识时间到！快来百度翻译...',
					},
					{
						date: '3月25日',
						ldate: '农历二月十六',
						week: '周一',
						txt: '涨知识时间到！快来百度翻译...',
					},
				],
				currentindex:0,
			}
		},
		methods: {
			active(i) {
					
				if(this.currentindex==i){
					return 
				}
				this.currentindex=i
			}
		}
	}
</script>

<style lang="less">
	* {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}

	a {
		text-decoration: none;
	}

	.applet {
		width: 100%;
		height: 100%;
		background-color: #f1f2f6;
		position: relative;
		padding-bottom: 10px;

		.top {
			display: flex;
			justify-content: space-between;
			color: #6e6f73;
			font-size: 16px;
			font-weight: 400;
			border-bottom: 1px solid #d5d6da;
			padding: 25px 30px 10px;
		}

		.group {
			width: 100%;

			.group-1 {
				.top {
					border: 0;
					padding: 13px 30px;
				}

				.main {
					width: 90%;
					height: 80px;
					margin: 0 auto;
					background-color: #fff;
					border-radius: 20px;
					padding: 10px;
					display: flex;
					flex-direction: row;
					justify-content: space-around;
					padding-top: 20px;

					.txt {
						color: #000000;
						border-left: 3px solid blue;
						text-indent: 1em;
					}

					.time {
						display: flex;
						flex-direction: column;
					}
				}
			}
		}

		.new {
			position: fixed;
			width: 50px;
			height: 50px;
			background-color: #006afc;
			bottom: 50px;
			right: 20px;
			line-height: 45px;
			text-align: center;
			border-radius: 50%;
			color: #fff;
			font-size: 40px;
		}

		.active {
			.top {
				color: blue;
			}
		}

	}
</style>