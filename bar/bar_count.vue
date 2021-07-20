<template>
    <view class="bar_count">
      <view class="figure">
        <image :src="obj.image">
        <text class="tag" v-if="obj.tag && obj.tag != 0">{{obj.tag}}</text>
      </view>
      <view class="btn" @click="even_click(obj)"><text>去结算</text></view>
      <view class="content">
        <view class="count">
          <view class="price">{{obj.price}}</view>
          <view class="price_ago">{{obj.price_ago}}</view>
        </view>
        <view class="deliver">{{obj.deliver}}</view>
      </view>
    </view>
</template>

<script>
  import mixin from '@/mixins/component.js'
  export default {
    mixins: [mixin],
    props: {
      obj:{
        type:Object,
        default(){
          return{
            image: "/img/default.png",
            tag: 1,
            price: 29.98,
            price_ago: 30.55,
            deliver: 0.57,
          }
        }
      }
    },
    data() {
      return {
      }
    },
    methods: {
      even_click(o) {
        if (this.func) {
          this.func(o);
        }
      }
    }
  }
</script>

<style>

</style>
