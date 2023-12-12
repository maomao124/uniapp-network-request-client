<template>
	<view>
		<button type="primary" @click="request">点击调用/api/test/get</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			request()
			{
				uni.request({
					url:'http://localhost:9091/api/test/get',
					timeout:1000,
					data:{
						key:'123'
					},
					success: (resp) => {
						console.log("调用成功,返回数据为：",resp.data.data);
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
