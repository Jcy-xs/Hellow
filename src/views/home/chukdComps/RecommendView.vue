<!--
 * @Author: your name
 * @Date: 2021-03-05 16:16:50
 * @LastEditTime: 2021-03-05 16:53:46
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall01\src\views\home\chukdComps\RecommendView.vue
-->
<template>
<div class="recommend">
  <div v-for="(item, index) in recommends" :key="index" class="recommend-item">
    <a :href="item.link">
      <img :src="item.image" alt="">
      <div>{{item.title}}</div>
    </a>
  </div>
</div>
</template>

<script>
export default {
  name: "RecommendView",
  props: {
    recommends: {
      type: Array,
      default() {
        return []
      },
    },
  },
};
</script>

<style scoped>
.recommend {
  display: flex;
  width: 100%;
}

.recommend-item {
  flex: 1;
}

.recommend-item img {
  width: 65px;
  height: 65px;
}
</style>