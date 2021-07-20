<template>
	<view class="bar_ad">
		<view class="list">
			<view class="item" v-for="(o,i) in list" :key="i">
				<navigator :url="o.url">
					<view class="figure">
						<image :src="o.image" alt="">
					</view>
					<view class="title">{{o.title}}</view>
				</navigator>
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
				default() {
					return [
						{
							image: "/img/default.png",
							title:"这是一个标题这是一个标题这是一个标题这是一个标题这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						},
						{
							image: "/img/default.png",
							title:"这是一个标题",
							url:""
						}
					]
				}
			}
		},
		data() {
			return {};
		}
	}
</script>

<style>
</style>
