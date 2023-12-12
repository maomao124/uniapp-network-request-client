<template>
	<view>
		<button type="primary" @click="request">点击调用/api/test/post</button>
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
					url:'http://localhost:9091/api/test/post',
					timeout:1000,
					method:'POST',
					header:{
						'content-type':'application/x-www-form-urlencoded',
					},
					data:{
						key:'456'
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
