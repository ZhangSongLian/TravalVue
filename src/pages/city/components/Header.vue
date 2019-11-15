<template>
  <div>
    <div class='header'>
      城市选择
      <!-- 跳回到首页 -->
      <router-link to="/">
        <div class="go-back iconfont">
          &#xe624;
        </div>
      </router-link>
      </div>
  </div>
</template>

<script>
  export default {
    name: 'CityHeader'
  }
</script>

<style lang="stylus" scoped>
 @import '~styles/varibles.styl';
  .header{
    height 0.86rem;
    line-height 0.86rem;
    text-align center;
    color #fff;
    background $bgColor;
    position relative;
  }
  .go-back {
    width 0.64rem;
    text-align center;
    font-size .35rem;
    color #fff;
    position absolute;
    left 0;
    top 0;
  }
</style>
