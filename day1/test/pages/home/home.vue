<template>
	<view>
		<button @click="chooseImage">选择图片</button>
		<image :src="imgSrc"></image>
		<button @click="getLocation">获取定位</button>
		<button @click="findContacts">获取联系人方式</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgSrc: ""
			};
		},
		methods: {
			chooseImage() {
				var self = this;
				uni.chooseImage({
					count: 6,
					success(res) {
						self.imgSrc = res.tempFilePaths[0]
						console.log(JSON.stringify(res))
					}
				})
			},
			getLocation() {
				uni.chooseLocation({
					success: function(res) {
						console.log('位置名称：' + res.name);
						console.log('详细地址：' + res.address);
						console.log('纬度：' + res.latitude);
						console.log('经度：' + res.longitude);
					}
				});
			},
			findContacts() {
				plus.contacts.getAddressBook(plus.contacts.ADDRESSBOOK_PHONE, function(addressbook) {
					addressbook.find(null, function(contacts) {
						console.log(JSON.stringify(contacts));
					}, function() {
						console.log(contacts.length);
					}, {
						multiple: true
					});
				}, function(e) {
					console.log("Get address book failed: " + e.message);
				});
			}
		}
	}
</script>

<style>

</style>
