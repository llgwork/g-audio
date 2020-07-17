# g-audio
\<template><br>
	\<view><br>
    \<view><br>
      \<view>src -> url\</view><br>
      \<view>showDuration -> 是否显示时长（默认显示）\</view><br>
      \<view>text -> 默认文字\</view><br>
      \<view>block -> 线性或模块（默认线性）\</view><br>
    \</view><br>
    \<view><br>
      \<g-audio :src="audio" :showDuration="true">\</g-audio><br>
    \</view><br>
	\</view><br>
\</template><br>

\<script><br>
	import gAudio from '@/components/g-audio/g-audio.vue';<br>
	export default {<br>
		components: {<br>
			gAudio<br>
		},<br>
		data() {<br>
			return {<br>
				audio: 'url'<br>
			}<br>
		},<br>
		onLoad() {<br>
<br>
		},<br>
		methods: {<br>
<br>
		}<br>
	}<br>
\</script><br>
\<style><br>
\</style><br>
