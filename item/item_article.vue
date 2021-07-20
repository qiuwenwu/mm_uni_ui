<template>
  <!-- 文章 -->
  <mm_item :url="obj[vm.url]">
    <view class="item_article" :class="css">
      <view class="media">
        <mm_icon :src="obj[vm.image]" :desc="obj[vm.tip]"></mm_icon>
      </view>
      <view class="doc">
        <view class="title" v-if="obj[vm.title]">
          <text class="h4">{{ obj[vm.title] }}</text>
          <text class="tag" v-if="obj[vm.tag]">{{ obj[vm.tag] }}</text>
        </view>
        <view class="content">
          <view class="desc" v-if="obj[vm.description]">{{ obj[vm.description] }}</view>
          <view class="source" v-if="obj[vm.source]">{{ obj[vm.source] }}</view>
          <view class="num_comment" v-if="obj[vm.num_comment]">{{ obj[vm.num_comment] }}</view>
          <view class="time" v-if="obj[vm.create_time]">{{ $to_time(obj[vm.create_time]) }}</view>
          <view class="collect" v-if="obj[vm.collect] && show" @click="run('collect', obj)">
            <text class="fa fa-heart" v-bind:class="{ 'font-default': obj[vm.collect] }"></text>
            <text>{{ obj[vm.collect] }}</text>
          </view>
          {{ obj[vm.content] }}
        </view>
      </view>
    </view>
  </mm_item>
</template>

<script>
  import mixin from '@/mixins/item.js'

  export default {
    mixins: [mixin],
    props: {
      uid: {
        type: Number,
        default: 0
      },
      show: {
        type: Boolean,
        default: true
      },
      field: {
        type: String,
        default: "id"
      }
    },
    methods: {
      click_fun(o) {
        var u = obj[this.vm.url];
        if (this.func) {
          if (!this.func(o)) {
            return;
          }
        }
        if (u) {
          this.$nav(u);
        }
      },
      has_collect(arr) {
        if (arr) {
          if (this.uid && arr) {
            return arr.has(this.field, this.uid);
          }
        }
        return false;
      }
    }
  }
</script>

<style>
</style>
