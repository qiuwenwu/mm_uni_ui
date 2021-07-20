<template>
	<!-- 轮播图 -->
	<view class="swiper_card swiper-container" :id="id">
		<view class="swiper-wrapper">
			<view class="swiper-slide" v-for="(o, idx) in list" :key="idx">
				<view class="card">
					<slot :row="o" :index="idx"></slot>
				</view>
			</view>
		</view>
		<view class="swiper-pagination"></view>
	</view>
</template>

<script>
	import mixin from '@/mixins/component.js';

	export default {
		mixins: [
			mixin
		],
		props: {
			id: {
				type: String,
				default: "id"
			}
		},
		methods: {
			doing() {
				var swiper = new this.$Swiper("#" + this.id, {
					speed: 350,
					autoplay: {
						delay: 2800,
						disableOnInteraction: false,
						waitForTransition: false,
					},
					centeredSlides: true,
					slidesPerView: 1.2,
					spaceBetween: 16,
					pagination: {
						el: '.swiper-pagination',
						clickable: true,
						dynamicBullets: true,
					}
				});
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
	.swiper_card .swiper-slide {
		width: calc(100% - 4rem);
		padding: 1rem 0 3rem 0;
		height: 15rem;
	}

	.swiper_card .mm_icon {
		width: 100%;
		border-radius: 0.25rem;
		height: 10rem;
		margin: auto;
	}

	.swiper_card .card {
		height: 100%;
	}
</style>
