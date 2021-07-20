<template>
	<!-- 快捷导航 -->
	<view class="nav_quick">
		<view class="btn_quick" @click="show_drop()">
			<slot>快捷导航</slot>
		</view>
		<view class="dropdown" :class="{show_drop:is_show}">
			<view class="item" v-for="(o,i) in list" :key="i">
				<view class="title"><text>{{o.title}}</text></view>
				<view class="list_sub">
					<view class="item_sub" v-for="(obj,idx) in o.sub" :key="idx">
						<navigator class="title" :url="obj.url">
							{{obj.title}}
						</navigator>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import mixin from '@/mixins/component.js'
	export default {
		mixins: [mixin],
		props: {
			list: {
				type: Array,
				default () {
					return [{
							title: "娱乐",
							sub: [{
								title: "舞蹈",
								url: "#"
							}, {
								title: "脱口秀",
								url: "#"
							}, {
								title: "音乐",
								url: "#"
							}, {
								title: "户外",
								url: "#"
							}, {
								title: "音乐",
								url: "#"
							}, {
								title: "户外",
								url: "#"
							}]
						},{
							title:"游戏",
							sub: [{
								title: "舞蹈",
								url: "#"
							}, {
								title: "脱口秀",
								url: "#"
							}]
						}]
				}
			},
		},
		data(){
			return{
				is_show:false
			}
		},
		methods:{
			show_drop(){
				this.is_show =! this.is_show;
			}
		}
	};
</script>

<style scoped>
</style>
