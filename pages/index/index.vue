<template>
	<view>
		<g-audio :src="audio" :showDuration="true"></g-audio>
	</view>
</template>

<script>
	import gAudio from '@/components/g-audio/g-audio.vue';
	export default {
		components: {
			gAudio
		},
		data() {
			return {
				audio: 'url'
			}
		},
		onLoad() {

		},
		methods: {
			
		}
	}
</script>

<style>
	
</style>
