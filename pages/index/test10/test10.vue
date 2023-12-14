<template>
	<view>
		<button type="primary" @click="conn">发起websocket连接</button>
		<button type="primary" @click="onConn">注册websocket连接打开事件</button>
		<button type="primary" @click="onConnError">注册websocket连接错误事件</button>
		<button type="primary" @click="send()">发送消息</button>
		<button type="primary" @click="closeConn()">关闭websocket连接</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			conn() {
				const userId = "10000001";
				uni.connectSocket({
					url: 'ws://localhost:9091/websocket/' + userId,
					method: 'GET',
					success: (resp) => {
						console.log(resp);
						uni.showToast({
							title: '连接成功',
							icon: 'success'
						})
					},
					fail: (err) => {
						console.log(err);
						uni.showToast({
							title: '连接失败',
							icon: 'error'
						})
					}
				})
			},
			onConn()
			{
				console.log("注册websocket连接打开事件");
				uni.onSocketOpen(function(res)
				{
					console.log("连接已打开");
					console.log(res);
				})
			},
			onConnError()
			{
				console.log("注册websocket连接错误事件");
				uni.onSocketError(function(err)
				{
					console.log('连接错误');
					console.log(err);
				});
			},
			send()
			{
				console.log("发送消息");
				uni.sendSocketMessage({
					data:'hello',
					success: (resp) => {
						console.log(resp);
						uni.showToast({
							title: '发送成功',
							icon: 'success'
						})
					},
					fail: (err) => {
						console.log(err);
						uni.showToast({
							title: '发送失败',
							icon: 'error'
						})
					}
				})
			},
			closeConn()
			{
				console.log("关闭连接");
				uni.closeSocket({
					success: (resp) => {
						console.log(resp);
						uni.showToast({
							title: '关闭成功',
							icon: 'success'
						})
					},
					fail: (err) => {
						console.log(err);
						uni.showToast({
							title: '关闭失败',
							icon: 'error'
						})
					}
				})
			}
		}
	}
</script>

<style>
button
{
	margin: 10px;
}
</style>