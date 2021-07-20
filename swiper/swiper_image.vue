<template>
	<!-- 轮播图 -->
	<view class="swiper_image">
		<view class="swiper-container" :id="id" >
			<swiper class="swiper swiper-wrapper">
				<swiper-item class="swiper-slide" v-for="(o, idx) in list" :key="idx">
					<slot :row="o" :index="idx"></slot>
				</swiper-item>
			</swiper>
			<view class="swiper-button-prev"></view>
			<view class="swiper-button-next"></view>
			<view class="swiper-pagination"></view>
		</view>
	</view>

</template>

<script>
	import mixin from '@/mixins/component.js';

	export default {
		mixins: [mixin],
		props: {
			id: {
				type: String,
				default: "id"
			}
		},
		methods: {
			doing() {
				// var swiper = new this.$Swiper('#' + this.id, {
				// 	speed: 350,
				// 	autoplay: {
				// 		delay: 2800,
				// 		disableOnInteraction: false,
				// 		waitForTransition: false,
				// 	},
				// 	centeredSlides: true,
				// 	slidesPerView: 1,
				// 	pagination: {
				// 		el: '.swiper-pagination',
				// 		clickable: true,
				// 		dynamicBullets: true,
				// 	},
				// 	navigation: {
				// 		nextEl: '.swiper-button-next',
				// 		prevEl: '.swiper-button-prev',
				// 	},
				// });
			}
		},
		onShow() {
			setTimeout(() => {
				this.doing()
			}, 300)
		}
	}
</script>

<style>
	.swiper_image .swiper-slide {
		width: calc(100% - 4rem);
		padding: 1rem 0 3rem 0;
		height: 18.75rem;

	}

	.swiper_image .swiper-container {
		user-select: none;
	}

	.swiper_image .mm_icon {
		width: 100%;
		border-radius: 0.25rem;
		height: 10rem;
		margin: auto;
	}
</style>
