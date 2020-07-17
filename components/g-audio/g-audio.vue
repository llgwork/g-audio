<template>
	<view class="x-audio-wrap" :class="{inline:!block}" ref="wrap" @click="play">
		<view class="x-sector" :class="{play:animate}">
			<view class="x-dot"></view>
		</view>
		<view class="x-time">{{duration&&showDuration?duration:text}}</view>
	</view>
</template>

<script>
	export default {
		name:'g-audio',
		props:{
			src:{
				type:String,
				default:''
			},
			text:{
				type:String,
				default:"轻触播放"
			},
			showDuration:{
				type:Boolean,
				default:true
			},
			block:{
				type:Boolean,
				default:false
			},
		},
		data() {
			return {
				audio:null,
				animate:false,
				timer:null,
				duration:null
			};
		},
		mounted(){
			this.audio=new Audio()
			this.audio.src=this.src
			this.audio.addEventListener('canplaythrough',()=>{
				this.duration=this.format(this.audio.duration)
			})
			this.audio.onplay=()=>{
				this.animate=true
				this.timer=setInterval(() => {
					this.animate=false
					setTimeout(()=>{
						this.animate=true
					},50)
				}, 1250);
			}
			this.audio.onpause=()=>{
				this.animate=false
				this.timer&&clearInterval( this.timer)
			}
			this.audio.onended=()=>{
				this.animate=false
				this.timer&&clearInterval( this.timer)
			}
			if(!window.GaudioList){
				window.GaudioList = []
			}
			window.GaudioList.push(this.audio)
		},
		methods:{
			play(){
				window.GaudioList.forEach(audio=>{
					audio.pause()
				})
				if(this.audio.paused){
					this.audio.play()
				}else{
					this.audio.pause()
				}
			},
			format(s){
				return s.toFixed(0)+"s";
			},
		}
	}
</script>

<style lang="scss" scoped>
.x-audio-wrap{
    height: 30px;
    width: 110px;
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    cursor: pointer;
    box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.25);
	background: #72c736;
    .x-sector{
        height: 7px;
        width: 7px;
        border-radius:4px 10px;
        border-right: 2px solid #ddd;
        border-top: 2px solid #ddd;
        transform: rotate(45deg);
        position: relative;
        margin-left: 10px;
        .x-dot{
            height: 4px;
            width: 4px;
            border-radius: 4px;
            background: #ddd;
            position: absolute;
            top: 4px;
        }
    }
    .x-sector::before{
        content: "";
        height: 9px;
        width: 9px;
        border-radius:4px 12px;
        border-right: 2px solid #ddd;
        border-top: 2px solid #ddd;
        transform: rotate(0deg);
        position: absolute;
        right: -7px;
        top: -7px;
    }
    .x-sector::after{
        content: "";
        height: 12px;
        width: 12px;
        border-radius:4px 14px;
        border-right: 2px solid #ddd;
        border-top: 2px solid #ddd;
        transform: rotate(0deg);
        position: absolute;
        right: -13px;
        top: -13px;
    }
    
    .x-time{
        color: #ffffff;
        font-size: 12px;
        margin-right: 10px;
    }
    &.inline{
        display: inline-flex
    }
}

@keyframes play-dot{
    from{
        background: #ddd
    }
    to{
        background: #5cadff
    }
}
@keyframes play-sector{
    from{
        border-color: #ddd
    }
    to{
        border-color: #5cadff
    }
}
.x-sector.play{
    animation: play-sector 0.3s 0.1s ease-in-out;
}
.x-sector.play::before{
    animation: play-sector 0.3s 0.2s ease-in-out;
}
.x-sector.play::after{
    animation: play-sector 0.3s 0.3s ease-in-out;
}
.x-sector.play .x-dot{
    animation: play-dot 0.3s ease-in-out;
}
</style>
