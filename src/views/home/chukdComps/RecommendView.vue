<!--
 * @Author: your name
 * @Date: 2021-03-05 16:16:50
 * @LastEditTime: 2021-03-05 17:11:50
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
  text-align: center;
  font-size: 12px;
  padding: 10px 0 15px;
  border-bottom: 8px solid #eee;
}

.recommend-item {
  flex: 1;
}

.recommend-item img {
  width: 100%;
  margin-bottom: 10px;
}
</style>