<template>
	<view>
		<p v-text="name"></p>
		<input v-model="name" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: "老姚"
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
