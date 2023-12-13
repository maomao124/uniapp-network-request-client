<template>
	<view>
		<button type="primary" @click="conn">发起websocket连接</button>
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
			}
		}
	}
</script>

<style>

</style>