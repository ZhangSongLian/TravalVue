<template>
  <div id="app">
    <!--#显示当前路由对应的内容-->
    <!--//Detail页面不做缓存-->
    <!-- 问题：设置了exclude="Detail"后，详情页中渐隐渐现的header效果不显示了 -->
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
