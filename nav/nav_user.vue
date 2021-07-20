<template>
	<view class="nav_user">
		<view class="login" v-if="!obj[vm.username]">
			<router-link to="/login"><text>登录</text></router-link>
			<router-link to="/register"><text>注册</text></router-link>
		</view>
		<view class="user" v-else :class="{active:is_active}" @click="active">
			<view class="username">
				<text>{{obj[vm.username]}}</text>
				<text class="icon"></text>
			</view>
			<view class="dropdown">
				<router-link :to="o.url" v-for="(o,i) in list" :key="i">
					<view class="title"><text>{{o[vm.title]}}</text></view>
				</router-link>
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
				default: function() {
					return [{
						title: "个人信息",
						url: ""
					}, {
						title: "账号管理",
						url: ""
					}, {
						title: "修改密码",
						url: ""
					}, {
						title: "退出",
						url: ""
					}]
				}
			},
			obj: {
				type: Object,
				default: function() {
					return {
						username: "姓名xxx",
						url: ""
					}
				}
			}
		},
		data() {
			return {
				key_drop: -1,
				is_active: false
			};
		},
		methods: {
			active() {
				this.is_active = !this.is_active
			}
		}
	}
</script>

<style>
</style>
