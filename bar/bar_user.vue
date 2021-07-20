<template>
	<view class="bar_user" @click="event_click(obj)">
		<view class="media">
			<mm_icon :src="obj[vm.image]" :desc="obj[vm.image]"></mm_icon>
		</view>
		<view class="doc">
			<view class="name"><text>{{obj.name}}</text></view>
			<text class="chevron"></text>
			<text class="qrcode"></text>
			<view class="account"><text>{{obj.user_id}}</text></view>
      <slot></slot>
		</view>
	</view>
</template>

<script>
	import mixin from '@/mixins/component.js'
	export default {
		mixins: [mixin],
		props: {
			obj: {
				type: Object,
				default() {
					return {
						image: "/img/default.png",
						name: "Tao",
						user_id: "123456",
						url:"#",
					}
				}
			}
		},
		data() {
			return {};
		},
    methods:{
      event_click(o){
        if (this.func) {
        	this.func(o);
        }
      }
    }
	}
</script>

<style>
</style>
