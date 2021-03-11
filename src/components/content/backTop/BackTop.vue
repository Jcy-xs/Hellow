<!--
 * @Author: your name
 * @Date: 2021-03-11 10:43:36
 * @LastEditTime: 2021-03-11 10:48:53
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall01\src\components\content\backTop\BackTop.vue
-->
<template>
  <div class="back-top">
    <img src="~assets/img/common/top.png" alt="">
  </div>
</template>

<script>
export default {
name: "BackTop"
}
</script>

<style scoped>
  .back-top {
    position: fixed;
    right: 8PX;
    bottom: 50PX;
  }

  .back-top img {
    height: 43px;
    width: 43px;
  }
</style>