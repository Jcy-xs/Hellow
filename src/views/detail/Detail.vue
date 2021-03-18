<!--
 * @Author: your name
 * @Date: 2021-03-16 09:12:44
 * @LastEditTime: 2021-03-17 16:08:16
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall01\src\views\detail\Detail.vue
-->
<template>
  <div id="detail">
    <detail-nav-bar class="detail-nav"></detail-nav-bar>
    <scroll class="content" ref="scroll">
      <detail-swiper :top-images="topImages"></detail-swiper>
      <detail-base-info :goods="goods"></detail-base-info>
      <detail-shop-info :shop="shop"></detail-shop-info>
      <detail-goods-info :detail-info="detailInfo" @imageLoad="imageLoad"></detail-goods-info>
      <detail-param-info :param-info="paramInfo"></detail-param-info>
      <detail-comment-info :comment-info="commentInfo"></detail-comment-info>
      <goods-list :goods="recommends"></goods-list>
    </scroll>
    
  </div>
</template>

<script>
import DetailNavBar from "./childComps/DetailNavBar.vue";

import { getDetail, Goods, Shop, GoodsParam, getRecommend } from "network/detail";
import DetailSwiper from './childComps/DetailSwiper.vue';
import DetailBaseInfo from './childComps/DetailBaseInfo.vue';
import DetailShopInfo from './childComps/DetailShopInfo.vue';
import Scroll from '../../components/common/scroll/Scroll.vue';
import DetailGoodsInfo from './childComps/DetailGoodsInfo.vue';
import DetailParamInfo from './childComps/DetailParamInfo.vue';
import DetailCommentInfo from './childComps/DetailCommentInfo.vue';
import GoodsList from '../../components/content/goods/GoodsList.vue';


export default {
  components: { 
    DetailNavBar, 
    DetailSwiper, 
    DetailBaseInfo, 
    DetailShopInfo, 
    Scroll, 
    DetailGoodsInfo, 
    DetailParamInfo,
    DetailCommentInfo,
    GoodsList, 
     },
  name: "Detail",
  data() {
    return {
      iid: null,
      topImages: [],
      goods: {},
      shop: {},
      detailInfo: {},
      paramInfo: {},
      commentInfo: {},
      recommends: []
    };
  },
  created() {
    //1.保存传入的iid
    this.iid = this.$route.params.iid;
    //2.根据iid请求详情数据
    getDetail(this.iid).then((res) => {
      //1.获取顶部的图片轮播数据
      const data = res.result;
      this.topImages = res.result.itemInfo.topImages;
      //2.获取商品信息
      this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services);
      //3.创建店铺信息
      this.shop = new Shop(data.shopInfo);
      //4.保存商品的详情数据
      this.detailInfo = data.detailInfo;
      //5.获取参数信息
      this.paramInfo = new GoodsParam(data.itemParams.info, data.itemParams.rule);
      //6.取出评论信息
      if (data.rate.cRate !== 0) {
        this.commentInfo = data.rate.list[0]
      }
    });
    //3.请求推荐数据
    getRecommend().then(res => {
      this.recommends = res.data.list
    })
  },
  methods: {
    imageLoad() {
      this.$refs.scroll.refresh()
    }
  }
};
</script>

<style scoped>
  #detail {
    position: relative;
    z-index: 9;
    background-color: #fff;
    height: 100vh;
  }
  .content {
    height: calc(100% - 44px);
    overflow: hidden;
  }
  .detail-nav {
    position: relative;
    z-index: 9;
    background-color: #fff;
  }
</style>