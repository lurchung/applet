<template>

<view class="main">
	
	<view class="banner">
						
						<swiper :indicator-dots="true" :autoplay="true" :interval="8000" :duration="1000">
							<swiper-item v-for="(item,index) in bannerList" :key="index">
								<img :src="item.url" alt="" width="100%" height="120px">
							</swiper-item>
						</swiper>
	</view>

	
	
	<view class="Home">
			<navigator url="/pages/register/register" class="frist">
				<view class="denglu">
					<view class="denglu-imgbox1">
						<img  class="img1" src="static/images-hmy/登录.png" alt="" width="30px"
						height="30px">
					</view>
					<view class="denglu-box">
						登录
					</view>
				</view>
			</navigator>
			<navigator url="/pages/timetable/timetable"><view class="denglu">
					<view class="denglu-imgbox2">
						<img src="static/images-hmy/课程表.png" alt="" width="100%"
						height="100%"/>
					</view>
					<view class="denglu-box2">
						课程表
					</view>
				</view></navigator>
			<navigator url="/pages/schedule/schedule"><view class="denglu">
					<view class="denglu-imgbox3">
						<img class="img3" src="static/images-hmy/日程 (1).png" alt="" width="25px"
						height="25px"/>
					</view>
					<view class="denglu-box3">
						日程
					</view>
				</view></navigator>
			<navigator url="/pages/new-schedule/new-schedule"><view class="denglu">
					<view class="denglu-imgbox4">
						<img class="img4" src="static/images-hmy/新建日程.png" alt="" width="25px"
						height="25px"/>
					</view>
					<view class="denglu-box4">
						新建日程
					</view>
				</view></navigator>
	</view>
	
	<view class="title1">
		<text class="text1">今日课表</text>
		
		<navigator url="/pages/timetable/timetable"  class="text2">查看更多></navigator>
		
	</view>

    <view class="content1">
		<scroll-view  scroll-y="true" class="scroll-view-1" >
							<view  class="scroll-1" style="border-bottom:1px black solid ;">
								<view class="box1" >
									<text class="text1">XXXX课程</text>
								</view>
								<view class="box2">
		                            <view class="box-text1">XXX节-XXX节</view>
								    <view class="box-text2">XXXX老师</view>
								</view>
							</view>
							
							<view  class="scroll-1">
								<view class="box1">
									<text class="text1">XXXX课程</text>
								</view>
								<view class="box2">
							        <view class="box-text1">XXX节-XXX节</view>
								    <view class="box-text2">XXXX老师</view>
								</view>
							</view>
							
							
								
							<view  class="scroll-1" style="border-bottom:1px black solid ;">
								<view class="box1" >
									<text class="text1">XXXX课程</text>
								</view>
								<view class="box2">
							        <view class="box-text1">XXX节-XXX节</view>
								    <view class="box-text2">XXXX老师</view>
								</view>
							</view>
							
							<view  class="scroll-1">
								<view class="box1">
									<text class="text1">XXXX课程</text>
								</view>
								<view class="box2">
							        <view class="box-text1">XXX节-XXX节</view>
								    <view class="box-text2">XXXX老师</view>
								</view>
							</view>
							
								
							
		</scroll-view>
		
	</view>


    <view class="title1">
		<text class="text1">今日日程</text>
		<navigator url="/pages/schedule/schedule" class="text2">查看更多></navigator>
		
	</view>
	
	<view class="content1">
		<scroll-view  scroll-y="true" class="scroll-view-1" >
							<view  class="scroll-1" style="border-bottom:1px black solid ;">
								<view class="box1" >
									<text class="text1">XXXXXXXX</text>
								</view>
								<view class="box2">
		                            <view class="box-text3">截止到XXXX</view>
								</view>  
							</view>
							
							<view  class="scroll-1">
								<view class="box1" >
									<text class="text1">XXXXXXXX</text>
								</view>
								<view class="box2">
								    <view class="box-text3">截止到XXXX</view>
								</view> 
							</view>
							
							
								
							<view  class="scroll-1" style="">
								<view class="box1" >
									<text class="text1">XXXXXXXX</text>
								</view>
								<view class="box2">
								    <view class="box-text3">截止到XXXX</view>
								</view> 
							</view>
							
							<view  class="scroll-1">
								<view class="box1" >
									<text class="text1">XXXXXXXX</text>
								</view>
								<view class="box2">
								    <view class="box-text3">截止到XXXX</view>
								</view> 
							</view>
							
								
							
		</scroll-view>
		
	</view>
	
	
	
    
    


	
</view>	
</template>

<script>
	
	 
	
	
	
	export default {
			data() {
				return {
					// 假设后端返回的数据长这个样子
					bannerList: [{
						url: "static/images-hmy/中国海洋大学.jpg"
					},
					{
						url: "https://ts1.cn.mm.bing.net/th/id/R-C.c125db9c9d102fb16a9365c69daa82c7?rik=zuQ8gDRsOrTpGw&riu=http%3a%2f%2fwww.liuxuehr.com%2f2018gxzp%2fzghydx%2fimages%2fpic5.jpg&ehk=Bj15zVXQhDYLNTyA%2fG4iDPeQi20KWyhCeMH07Rfi68o%3d&risl=&pid=ImgRaw&r=0"
					}, {
						url: "https://id.ouc.edu.cn/sso/casLogin/img/banner16-1694742541774.jpg"
					},  ]
				}
			},
		}
		
		;
		
		
		
</script>

<style lang="less">
	.main{
		width: 100%;
		
		
		}
	.Home{
		margin: 0 0 10% 0;
		width: 100%;
		
		display: flex;
	}
	
	.Home navigator {
		width: 50px;
		height: 50px;
		margin: 0 auto;
	}
    .banner {
		width: 100%;
		height: 120px;
		margin: 0 0 5% 0;
	}
	swiper {
		width: 100%;
		height: 100%;
	}
	
	.title1{
		margin-top: 10px;
		height: 15px;
		font-size: 5px;
		width: 88%;
		
		margin: 0 auto 2%;
		
	}
	
	.text1 {
		text-align: left;
		font-weight: 600;
	}
	
	.text2 {
		float: right;
		font-weight: 600;
	}
		
	.content1{
		width: 80%;
		height: 100px;
		margin: 0 auto 10%;
		
	}
	
	.scroll-view-1{
		width: 100%;
		height: 110px;
		border: 1px black solid;
		
		
	}
	
	.scroll-1{
		width: 100%;
		height: 54px;
		overflow: hidden;
		display: flex;
		justify-content: space-between;
		background-color: rgba(0,0,0,0.08);
		
		
	}
	.box1{
		margin:  auto 3%;
		margin-right: 0;
	}
	
	.box2{
		font-size: 14px;
		margin:  auto 3%;
	}
	.box-text1{
		margin-bottom: 8%;
	}
	
	.box-text2{
		float: right;
	}
	
	.box-text3{
		float: right;
	}
	
	.frist {
		width: 10%;
		height: 30px;
		
	}
	
	.denglu {
		
		
		width: 100%;
		height: 100%;
		
	}
	
	.denglu-imgbox1 {
		background-color: rgba(86, 199, 191);
		transform: translate(10px,0);
		width: 40px;
		height: 40px;
		border-radius: 50%;
	}
	
	.img1 {
		transform: translate(3px,5px);
	}
	
	.denglu-box {
		font-size: 8px;
		color: rgba(48, 49, 51);
		transform: translate(18px,0);
		font-weight: 600;
		
	}
	
	
	
	
	
	
	.denglu-imgbox2 {
		background-color: rgba(51, 181, 229);
		transform: translate(10px,0);
		width: 40px;
		height: 40px;
		border-radius: 50%;
	}
	
	.denglu-box2 {
		font-size: 8px;
		color: rgba(48, 49, 51);
		transform: translate(12.5px,0);
		font-weight: 600;
		
	}
	
	
	
	
	
	.denglu-imgbox3 {
		background-color: rgba(255, 154, 18);
		transform: translate(10px,0);
		width: 40px;
		height: 40px;
		border-radius: 50%;
	}
	
	.denglu-box3 {
		font-size: 8px;
		color: rgba(48, 49, 51);
		transform: translate(18px,0);
		font-weight: 600;
		
	}
	
	.img3 {
		transform: translate(7px,7px);
	}
	
	
	
	
	
	
	
	.denglu-imgbox4 {
		background-color: rgba(225, 80, 79);
		transform: translate(10px,0);
		width: 40px;
		height: 40px;
		border-radius: 50%;
	}
	
	.denglu-box4 {
		font-size: 8px;
		color: rgba(48, 49, 51);
		transform: translate(5px,0);
		font-weight: 600;
		
	}
	
	.img4{
		transform: translate(7.5px,7px);
	}
	
	
	
	
</style>