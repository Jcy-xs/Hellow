<!--
 * @Author: your name
 * @Date: 2021-03-16 10:50:54
 * @LastEditTime: 2021-03-16 14:33:22
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall01\src\views\detail\childComps\DetailSwiper.vue
-->
<template>
    <swiper class="detail-swiper" >
      <swiper-item v-for="(item, index) in topImages" :key="index">
        <img :src="item" alt="">
      </swiper-item>
    </swiper>
</template>

<script>
import Swiper from '../../../components/common/swiper/Swiper.vue'
import SwiperItem from '../../../components/common/swiper/SwiperItem.vue'


export default {
  components: { Swiper, SwiperItem },
  name: "DetailSwiper",
  props: {
    topImages: {
      type: Array,
      default() {
        return []
      }
    }

  }
}
</script>

<style scoped>
  .detail-swiper {
    height: 300px;
    overflow: hidden;
  }
</style>