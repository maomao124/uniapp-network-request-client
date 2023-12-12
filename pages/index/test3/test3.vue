<template>
	<view>
		<button type="primary" @click="request">点击调用/api/test/post2</button>
		<br>
		<button type="primary" @click="request2">点击调用/api/test/post3</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			request() {
				uni.request({
					url: 'http://localhost:9091/api/test/post2',
					timeout: 1000,
					method: 'POST',
					header: {
						'content-type': 'application/x-www-form-urlencoded',
					},
					data: {
						key: '789'
					},
					success: (resp) => {
						console.log("调用成功,返回数据为：", resp.data.data);
						console.log(resp);
					},
					fail: (resp) => {
						console.log("调用失败");
						console.log(resp);
					}
				})
			},
			request2() {
				uni.request({
					url: 'http://localhost:9091/api/test/post3',
					timeout: 1000,
					method: 'POST',
					header: {
						'content-type': 'application/x-www-form-urlencoded',
					},
					data: {
						key: '789'
					},
					success: (resp) => {
						console.log("调用成功,返回数据为：", resp.data.data);
						console.log(resp);
					},
					fail: (resp) => {
						console.log("调用失败");
						console.log(resp);
					}
				})
			}
		}
	}
</script>

<style>

</style>