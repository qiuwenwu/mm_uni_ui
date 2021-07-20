<template>
	<view class="mm_nav">
		<view class="ul">
			<view class="li" v-for="(o, index) in list" :key="index"><navigator :url="o.url" v-if="o.url.indexOf('http:') === 0 || o.url.indexOf('https:') === 0">{{ o.title }}<text
					 class="message" v-show="o.message > 0">{{ o.message }}</text></navigator>
				<router-link :to="o.url" v-else>{{ o.title }}<text class="message" v-show="o.message > 0">{{ o.message }}</text></router-link>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			list: {
				type: Array,
				default() {
					return [];
				}
			},
			vm: {
				type: Object,
				default() {
					return {
						icon: "icon",
						title: "title",
						desc: "desc",
						url: "url",
						name: "name",
						tip: "tip"
					};
				}
			}
		}
	};
</script>

<style>
</style>
