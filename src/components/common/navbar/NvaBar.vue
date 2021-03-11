<!--
 * @Author: your name
 * @Date: 2021-03-04 14:55:12
 * @LastEditTime: 2021-03-10 14:52:41
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Xinde\supermall01\src\components\common\navbar\NvaBar.vue
-->
<template>
  <div class="nav-bar">
    <div class="left"><slot name="left"></slot></div>
    <div class="center"><slot name="center"></slot></div>
    <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
export default {
 name: "NavBar" 
}
</script>

<style scoped>
.nav-bar {
  display: flex;
  height: 44px;
  line-height: 44px;
  text-align: center;
  z-index: 9;
}

.left, .right {
  width: 60px;
}

.center {
  flex: 1;
}
</style>