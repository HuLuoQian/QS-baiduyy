<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view>
			<text class="title">{{title}}</text>
			<button type="primary" @tap="openVoice()">播放语音</button>
			<button type="primary" style="margin-top: 10px;" @tap="getAudioObject()">获取音频对象播放</button>
		</view>
	</view>
</template>

<script>
	import Voice from '@/QS-baiduyy/QS-baiduyy.js';
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			this.openVoice();
		},
		methods: {
			openVoice() {
				console.log('准备播报语音');
				Voice('你好，我是该插件的作者取舍');
				Voice('欢迎使用百度语音合成接口');
				Voice('祝您生活愉快, 万事顺利！');
				Voice('谢谢！');
			},
			async getAudioObject() {
				console.log('准备获取音频对象')
				const audio = await Voice({
					voiceSet: {
						tex: '返回了音频对象'
					},
					returnAudio: true
				})
				console.log('获取音频对象')
				audio.onPlay(()=>{
					console.log('音频开始播放了')
				})
				audio.play();
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
