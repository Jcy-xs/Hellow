<!--
 * @Author: your name
 * @Date: 2021-03-04 10:24:16
 * @LastEditTime: 2021-03-15 17:14:18
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Xinde\supermall01\src\App.vue
-->
<template>
  <div id="app">
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
    <main-tab-bar></main-tab-bar>
  </div>
</template>

<script>
import MainTabBar from './components/content/mainTabbar/MainTabBar.vue'


export default {
  name: 'App',
  components: {
    MainTabBar
  }
}
</script>

<style>
  @import "assets/css/base.css";
</style>
