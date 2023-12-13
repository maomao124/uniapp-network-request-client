<template>
	<view>
		<button type="primary" @click="download">下载文件</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			download() {
				uni.downloadFile({
					url: 'http://localhost:9091/api/test/download',
					timeout: 1000,
					success: (resp) => {
						console.log(resp);
						console.log("文件下载成功，位于临时目录", resp.tempFilePath);
					},
					fail: (err) => {
						console.log(err);
						console.log("下载失败");
					}
				})
			}
		}
	}
</script>

<style>

</style>