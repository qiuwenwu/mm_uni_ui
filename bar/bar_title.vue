<template>
	<!-- 标题栏 -->
	<view @click="event_click(obj)" class="bar_title">
		<view class="title"><text>{{obj.title}}</text></view>
		<view class="desc"><text>{{obj.desc}}</text></view>
	</view>

</template>

<script>
	import mixin from '@/mixins/component.js'
	export default {
		mixins: [mixin],
		props: {
			obj: {
				type: Object,
				default () {
					return {
						title: "标题",
						desc:"描述",
						url:"#"
					}
				}
			},
		},
		data() {
			return {};
		},
		methods:{
      event_click(obj){
      	if(this.func){
      		this.func(obj);
      	}
      }
		}
	}
</script>

<style>
</style>
