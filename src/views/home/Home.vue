<!--
 * @Author: your name
 * @Date: 2021-03-04 14:38:21
 * @LastEditTime: 2021-03-05 10:10:36
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Xinde\supermall01\src\views\home\Home.vue
-->
<template>
  <div id="home">
    <nva-bar class="home-nav"><div slot="center">购物街</div></nva-bar>
    <home-swioer :banners="banners"></home-swioer>
    <recommend-view></recommend-view>
  </div>
</template>

<script>
import NvaBar from "../../components/common/navbar/NvaBar.vue";
import HomeSwioer from './chukdComps/HomeSwioer.vue';

import { getHomeMultidata } from "../../network/home";
import RecommendView from './RecommendView.vue';

export default {
  components: { NvaBar, HomeSwioer, RecommendView },
  name: "Home",
  data() {
    return {
      banners: [],
      recommends: [],
    };
  },
  created() {
    getHomeMultidata().then((res) => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  },
};
</script>

<style scoped>
.home-nav {
  background-color: var(--color-tint);
  color: aliceblue;
}
</style>
