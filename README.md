# g-audio
\<template>\<br>
	<view>
    <view>
      <view>src -> url</view>
      <view>showDuration -> 是否显示时长（默认显示）</view>
      <view>text -> 默认文字</view>
      <view>block -> 线性或模块（默认线性）</view>
    </view>
    <view>
      <g-audio :src="audio" :showDuration="true"></g-audio>
    </view>
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
