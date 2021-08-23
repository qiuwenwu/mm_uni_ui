<template>
	<view class="swiper_img">
		<swiper class="swiper" :indicator-color="indicatorColor" :indicator-active-color="indicatorActiveColor"
			:indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
			<swiper-item v-for="(o, i) in list" :key="i" @click="$nav(o.url)">
				<!-- <navigator :url="o[vm.url]"> -->
					<image class="image" v-if="o[vm.img]" :src="$fullImgUrl(o[vm.img])"></image>
					<text class="title" v-if="show_title && o[vm.title]">{{ o[vm.title] }}</text>
				<!-- </navigator> -->
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		props: {
			show_title: {
				type: String,
				default: ""
			},
			list: {
				type: Array,
				default: function() {
					return [];
				}
			},
			vm: {
				type: Object,
				default: function() {
					return {
						img: "img",
						title: "title"
					}
				}
			},
			interval: {
				type: Number,
				default: 4000
			},
			duration: {
				type: Number,
				default: 500
			},
			indicatorDots: {
				type: Boolean,
				default: false
			}
		},
		data() {
			return {
				background: ['color1', 'color2', 'color3'],
				indicatorColor: "rgba(0, 0, 0, .3)",
				indicatorActiveColor: "#fff",
				autoplay: true
			}
		},
		methods: {
			changeIndicatorDots(e) {
				this.indicatorDots = !this.indicatorDots
			},
			changeAutoplay(e) {
				this.autoplay = !this.autoplay
			},
			intervalChange(e) {
				this.interval = e.target.value
			},
			durationChange(e) {
				this.duration = e.target.value
			}
		}
	}
</script>

<style>
	.swiper_img .image {
		width: 100%;
		height: 100%;
	}

	.swiper_img .title {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		text-align: center;
	}
</style>
