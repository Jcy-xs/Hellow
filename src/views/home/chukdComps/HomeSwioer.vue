<!--
 * @Author: your name
 * @Date: 2021-03-04 17:43:18
 * @LastEditTime: 2021-03-15 16:13:53
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Xinde\supermall01\src\views\home\chukdComps\HomeSwioer.vue
-->
<template>
  <swiper>
      <swiper-item v-for="(item, index) in banners" :key="index">
        <a href="item.link">
          <img :src="item.image" alt="" @load="imageLoad"/>
        </a>
      </swiper-item>
    </swiper>
</template>

<script>
import { Swiper, SwiperItem } from 'components/common/swiper'

export default {
  name: "HomeSwiper",
  props: {
    banners: {
      type:   Array,
      default() {
        return []
      }
    }
  },
  data() {
    return {
      isLoad: false
    }
  },
  components: {
    Swiper,
    SwiperItem
  },

  methods: {
    imageLoad() {
      if (!this.isLoad) {
        this.$emit('swiperImageLoad')
        this.isLoad = true
      }
    }
  }
}
</script>

<style>

</style>