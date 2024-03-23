<template>
	<view class="login">
		<view class="login-title">OUCer校园助手</view>
		<view class="login-content">
			<view class="login-username">
				<i class="el-icon-user"></i>
				<input type="text" placeholder="请输入账号" v-model="phone">
			</view>
			<view class="login-password">
				<i class="el-icon-key"></i>
				<input type="safe-password" name="" id="" placeholder="请输入密码" v-model="password">
			</view>
		</view>
		<view class="button"><button @click="onsubmit">登录</button></view>
		<view class="login-botton">
			<view class="login-password" @click="findPassword">找回密码</view>
			<span>|</span>
			<view class="login-zhuce" @click="Registration">注册账号</view>
		</view>
		<!-- 其他的登录方式 -->
		<view class="login-other">
			<view class="login-top">
				其他的登录方式
			</view>
			<view class="login-icon">
				<image src="../../static/images/QQ.png" mode="widthFix"></image>
				<image src="../../static/images/weixin.png" mode="widthFix"></image>
			</view>
		</view>
	</view>
</template>

<script>
import { mapMutations } from 'vuex';
export default {
	data() {
		return {
			phone:'',
			password:'',
			rules: {
				phone: [{ required: true, message: '请输入手机号', rule: '/^1[23456789]\d{9}$/' }],
				password: [{ required: true, message: '请输入密码', trigger: 'blur' }]
			}
		};
	},
	methods: {
		// ...mapMutations(['user_Login']),
		//登录
		onsubmit() {
			if(this.phone==''||this.password==''){
				uni.showToast({
					title:"内容不能为空哦！",
					icon:"none"
				})
			}else{
				let data={
					phone:this.phone,
					password:this.password
				}
				uni.request({
					url: '/api/login/loginUser',
					method: 'POST',
					data: data,
					success: res => {
						console.log(res.data.data.data);
						if (res.data.code == 200) {
							this.$store.commit("userLogin",res.data.data.data );
							localStorage.setItem('status',true)
						 //页面跳转
							this.$router.push('/pages/index/index');
			
							uni.showToast({
								title: res.data.data.msg,
								icon: 'none'
						 });
						} else {
							uni.showToast({
								title: res.data.data.msg,
								icon: 'none'
							});
						}
					}
				});
				}
		},
		Registration() {
			console.log('hah ');
			uni.navigateTo({
				url: '../../pages/register/zhuce/zhuce'
			});
		},
		findPassword() {
			console.log('hah ');
			this.$router.push('/pages/login/findPassword');
		},
		loginOther(){
			uni.share({
				provider: "weixin",
				scene: "WXSceneSession",
				type: 1,
				summary: "",
				success: function (res) {
					console.log("success:" + JSON.stringify(res));
				},
				fail: function (err) {
					console.log("fail:" + JSON.stringify(err));
				}
			});

		}
	}
};
</script>

<style lang="less">
.login {
	 // background-image: linear-gradient(120deg, #05ee28, #6a3dad);
	 background-color: #fff;
	width: 100%;
	background-position: center;
	background-size: cover;
	// background-color: #464646;
	margin:0px;
	background-size:100% 100%;
	background-attachment:fixed;
	height: 1535rpx;
	opacity: 0.8;
	.login-title {
		padding-top: 150rpx;
		display: flex;
		justify-content: flex-start;
		margin-left: 50rpx;
		font-weight: 700;
		font-size: 40rpx;
		color: #2596ff;
		letter-spacing: 5rpx;
		margin-bottom: 50rpx;
	}
	.login-content{
		.login-username{
			display: flex;
			align-items: center;
		    margin: 0 50rpx;
			border-bottom: 1rpx solid gainsboro;
			input{
				padding: 10rpx;
				height: 60rpx;
				width: 80%;
			}
			i {
				color: #63c1ff;
				padding-right: 20rpx;
				font-size: 50rpx;
			}
		}
		.login-password{
			display: flex;
			align-items: center;
		    margin: 0 50rpx;
			border-bottom: 1rpx solid gainsboro;
			margin-top: 50rpx;
			input{
				padding: 10rpx;
				height: 60rpx;
				width: 80%;
			}
			i {
				color: #55aaff;
				padding-right: 20rpx;
				font-size: 50rpx;
			}
		}
	}
	.button{
		margin-top: 120rpx;
		
		button{
			background-color:#6999ff;
			width: 90%;
			height: 85rpx;
			text-align: center;
			line-height: 85rpx;
			color: #fff;
		}
	}
	.login-botton{
		display: flex;
		justify-content: center;
		margin-top: 100rpx;
		.login-password{
			padding: 0 15rpx;
			color: #63c1ff;
		}
		.login-zhuce{
			padding: 0 15rpx;
			color: #63c1ff;
		}
	}
	.login-other{
		position: absolute;
		bottom: 100rpx;
	    left: 37%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		.login-top{
			text-align:center;
		}
		.login-icon{
			display: flex;
			justify-content: space-between;
			margin-top: 50rpx;
			image{
				width: 80rpx;
			}
		}
	}
	
}
</style>



