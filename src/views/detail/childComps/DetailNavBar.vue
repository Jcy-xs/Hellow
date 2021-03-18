<!--
 * @Author: your name
 * @Date: 2021-03-16 09:30:13
 * @LastEditTime: 2021-03-16 15:03:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall01\src\views\detail\childComps\DetailNavBar.vue
-->
<template>
  <div>
    <nva-bar>
      <div slot="left" class="back" @click="backClick">
          <img src="~assets/img/common/back.svg" alt="">
      </div>
      <div slot="center" class="title">
        
        <div v-for="(item, index) in titles" :key="index" 
        class="title-item" 
        :class="{active: index === currentIndex}" @click="itemClick(index)">
        {{item}}
        </div>
      </div>
    </nva-bar>
  </div>
</template>

<script>
import NvaBar from '../../../components/common/navbar/NvaBar.vue'
export default {
  components: { NvaBar },
  name: "DetailNavBar",
  data() {
    return {
      titles: ['商品', '参数', '评论', '推荐'],
      currentIndex: 0
    }
  },
  methods: {
    itemClick(index) {
      this.currentIndex = index
    },
    backClick() {
      this.$router.go(-1)
    }
  }
}
</script>

<style scoped>
  .title {
    display: flex;
    font-size: 13px;
  }

  .title-item {
    flex: 1;
  }

  .active {
    color: var(--color-high-text);
  }
  .back img{
    margin-top: 10px;

  }
</style>