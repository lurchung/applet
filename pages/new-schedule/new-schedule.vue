<template>
	<view class="box">
       <view class="type">
		   <text class="selected">日程</text>
		   <text>生日</text>
		   <text>纪念日</text>
		   <text>倒数日</text>
	   </view>
	   <view class="schedule-name">
		   <input type="text" value="日程名称" />
	   </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

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

	.box{
		background-color: #f1f2f6;
		padding-bottom:10px;
		.type{
			display: flex;
			justify-content: space-around;
			padding:30px 0 10px;
			background-color: #f1f2f6;
			text{
				background-color: #dfe0e4;
				width: 70px;
				height: 30px;
				text-align: center;
				padding:5px 0;
				border-radius: 15px;
			}
			.selected{
				color:#fff;
				background-color: #006afc;
			}
		}
		.schedule-name{
			width: 90%;
			margin:20px auto;
			height: 65px;
			background-color: #fff;
			border-radius:15px;
			padding-top:18px;
			input{
				width: 90%;
				height: 25px;
				margin:0 auto;
				border-left:3px solid #006ef9;
				color:#969696;
			}
		}
	}
</style>