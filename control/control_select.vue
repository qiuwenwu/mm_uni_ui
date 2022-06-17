<template>
	<view class="control_select">
		<view class="title" v-if="title" v-html="title"></view>
		<view class="value" v-bind:class="{'disabled': disabled }">
			<picker :value="index" :range="options" :range-key="rangeKey" @change="set">
				<slot :data="options[index]">
					<view>{{ options[index].name }}</view>
				</slot>
			</picker>
		</view>
		<view class="tip" v-if="tip">{{ tip }}</view>
	</view>
</template>

<script>
	import mixin from "@/mixins/control.js";
	export default {
		mixins: [mixin],
		props: {
			rangeKey: {
				type: String,
				default: "name"
			},
			field: {
				type: String,
				default: "value"
			}
		},
		data() {
			return {
				index: 0
			}
		},
		methods: {
			set: function set(e) {
				var index = e.target.value;
				var value = this.options[index][this.field];
				this.index = index;
				this.$emit("input", value);
				if (this.value !== value) {
					this.$emit("change", index, value);
				}
			},
			click_fun: function click_fun(value) {
				this.$emit("input", value);
				this.func(value);
			},
			update_index() {
				var list = this.options;
				for (var i = 0; i < list.length; i++) {
					var o = list[i];
					if (o.value == this.value) {
						this.index = i;
						break;
					}
				}
			}
		},
		computed: {
			val_name: function val_name() {
				var k = this.field;
				var v = this.value;
				var lt = this.options;
				var name = "";

				for (var i = 0; i < lt.length; i++) {
					var o = lt[i];

					if (o[k] === v) {
						name = o.name;
						break;
					}
				}

				return name;
			}
		},
		created() {
			this.update_index();
			console.log("下表2", this.index);
		},
		watch: {
			value() {
				this.update_index();
			}
		}
	};
</script>

<style>
</style>
