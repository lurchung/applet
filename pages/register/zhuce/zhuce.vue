<template>
	<view class="registration">
		<view class="registration-content">
			<view class="login-username">
				<i class="el-icon-mobile"></i>
				<input type="text" name="" id="" placeholder="请输入手机号" v-model="phone" />
			</view>
			<view class="login-code">
				<i class="el-icon-cpu"></i>
				<input type="text" placeholder="请输入验证码" v-model="userCode" />
				<button type="warning" :disabled="disabled" @click="sendCode">{{ codeMsg }}</button>
			</view>
		</view>
		<view class="login-button"><button @click="login">下一步</button></view>
		<view class="registration-botton"><view class="registration-password" @click="goBack">密码登陆</view></view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			phone: '',
			userCode: '',
			disabled: false,
			codeNum: 10,
			codeMsg: '获取验证码',
			code: '',
			rules: {
				phone: {
					rule: '/^1[23456789]\d{9}$/',
					meg: '手机的格式不对'
				}
			}
		};
	},
	methods: {
		sendCode() {
			if (this.phone == '') {
				uni.showToast({
					title: '手机号不能为空',
					icon: 'none'
				});
			} else if (this.phone != '') {
				var reg = /^1[3456789]\d{9}$/;
				if (!reg.test(this.phone)) {
					uni.showToast({
						title: '输入有效的手机号',
						icon: 'none'
					});
				} else {
					//禁用按钮
					this.disabled = true;

					//发送请求
					uni.request({
						url: '/api/login/code',
						method: 'POST',
						data: {
							phone: this.phone
						},
						success: res => {
							console.log('11', res.data.data);
							if (res.data.data.success) {
								this.code = res.data.data.data;
							}
						}
					});
					//倒计时
					let timer = setInterval(() => {
						--this.codeNum;
						this.codeMsg = `重新发送 ${this.codeNum}`;
					}, 1000);
					//判断定时器停止
					setTimeout(() => {
						clearInterval(timer);
						(this.disabled = false), (this.codeMsg = '获取验证码'), (this.codeNum = 10);
					}, 10000);
				}
			}
		},
		//登录
		login() {
			if (this.code == '' || this.phone == '') {
				uni.showToast({
					title: '手机号不能为空',
					icon: 'none'
				});
			} else if (this.userCode == this.code) {
				//验证码正确
				uni.request({
					url: '/api/login/addUser',
					method: 'POST',
					data: {
						phone: this.phone
					},
					success: res => {
						//code 200 注册成功
						if (res.data.code == 200) {
							uni.showToast({
								title: res.data.data.msg,
								icon: 'none'
							});
							//给vuex添加数据
							this.$store.commit('userLogin', res.data.data.data);
							//路由跳转
							this.$router.push('/pages/index/index');
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
		//密码登录
		goBack() {
			this.$router.push('/pages/login/login');
		},
		validate(key) {
			let bool = true;
			if (!this.rules[key].rule.test(this[key])) {
				uni.showToast({
					title: this.rules[key].meg,
					icon: 'none'
				});
				bool = false;
				return false;
			}
			return bool;
		}
	}
};
</script>

<style lang="less">
.registration {
	width: 100%;
	background-position: center;
	background-size: cover;
	background-color: #fff;
	margin: 0px;
	background-size: 100% 100%;
	background-attachment: fixed;
	opacity: 0.8;
	// margin-top: 100rpx;
	.registration-content{
		display: flex;
		flex-direction: column;
		margin: 0 50rpx;
		input{
			padding: 10rpx;
			width:60%;
			height: 70rpx;
		}
		i {
			color: #6999ff;
			padding-right: 20rpx;
			font-size: 50rpx;
		}
		.login-username{
			display: flex;
			align-items: center;
			border-bottom: 1rpx solid gainsboro;
			margin-top: 30rpx;
		}
		.login-code{
			display: flex;
			align-items: center;
			border-bottom: 1rpx solid gainsboro;
			margin-top: 30rpx;
			button{
				width:250rpx;
				height: 85rpx;
				font-size: 30rpx;
				line-height: 85rpx;
				background-color: #2596ff;
				color: #fff;
			}
		}
	}
	.login-button{
		margin-top: 150rpx;
		width: 90%;
		margin-left: 5%;
		button{
			background-color: #6999ff;
			color: #fff;
		}
	}
}

.registration-botton {
	display: flex;
	margin-top: 50rpx;
	justify-content: space-between;
	.registration-password {
		padding-left: 40rpx;
		color: #fff;
	}
	.registration-zhuce {
		padding-right: 40rpx;

		color: #fff;
	}
}
</style>

