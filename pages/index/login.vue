<template>
	<view>
		<view class="status_bar"><!--状态栏--></view>
		<view class="head">
			<text class="text_1">登录</text>
		</view>
		<view>
			<input class="input_1" type="text" v-model="userinfo.phonenumbler" placeholder="手机号">
			<input class="input_1" type="safe-password" v-model="userinfo.password" placeholder="密码">
		</view>
		<view class=".read">
			<switch @change="readchange" style="transform: scale(0.5);"/>
			<text>已阅读并同意相关</text><text style="color: blue;border-bottom:solid;" @click="readchange">《用户协议》</text>
		</view>
		<button class="button_1" @click="login">登录</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userinfo:{
					phonenumbler:'',
					password:''
				},
				read:'',
				contrast:'ture'
			}
		},
		methods: {
			readchange(e){
				this.read = e.detail.value
			},
			readaggre(){
			},
			login(){
				//与数据库中数据比对，返回结果
				if(this.contrast){
					uni.setStorage({
						key: 'userinfo',
						data: this.userinfo,
						success: function () {
							uni.redirectTo({
								url:"/pages/index/index"
							})
						}
					});
				}
			}
		}
	}
</script>

<style>
	.status_bar{
		height: var(--status-bar-height);
	    width: 100%;
	}
	.head{
		margin: 40px;
		font-size: 36px;
		text-align: center;
	}
	.input_1{
		height: 30px;
		margin: 30px;
		padding-left: 10px;
		border-bottom: solid;
	}
	.button_1{
		margin: 50px;background-color:skyblue;
	}
	.read{
		padding:50px;
	}
</style>
