<template>
	<view>
		<button type="primary" @click="upload">上传图片</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			upload() {
				uni.chooseImage({
					success: (chooseImageRes) => {
						const tempFilePaths = chooseImageRes.tempFilePaths;
						uni.uploadFile({
							url: 'http://localhost:9091/api/test/upload',
							timeout:1000,
							filePath: tempFilePaths[0],
							name: 'file',
							success: (uploadFileRes) => {
								console.log(uploadFileRes.data);
							},
							fail: (err) => {
								console.log("上传失败", err);
							}
						});
					}
				});
			}
		}
	}
</script>

<style>

</style>