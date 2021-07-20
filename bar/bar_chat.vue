<template>
	<view class="bar_chat">
		<view class="btn_keyboard" @click="even_click(obj.keyboard)"><text class="icon_keyboard"></text></view>
		<view class="btn_voice" @click="even_click(obj.voice)"><text class="icon_voice"></text></view>
		<view class="input_box">
			<input type="text" :value="value" v-on:input="$emit('input', $event.target.value)">
			<text class="icon_smile" @click="even_click(obj.smile)"></text>
		</view>

		<view class="btn_more" @click="even_click(obj.more)"><text class="icon_more"></text></view>
	</view>
</template>

<script>
	import mixin from '@/mixins/component.js'
	export default {
		mixins: [mixin],
		model: {
			prop: 'value',
			event: 'input'
		},
		props: {
			value: {
				type: String,
				default: ""
			},
			obj: {
				type: Object,
				default () {
					return {
						keyboard: {
							title: "键盘",
							command: "keyboard"
						},
						voice: {
							title: "语音",
							command: "voice"
						},
						smile: {
							title: "表情",
							command: "smile"
						},
						more: {
							title: "更多",
							command: "more"

						}
					}
				}
			}
		},
		data() {
			return {};
		},
		methods: {
			even_click(o) {
				if (this.func) {
					this.func(o);
				}
			}
		}
	}
</script>

<style>

</style>
