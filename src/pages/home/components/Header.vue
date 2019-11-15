<template>
  <div class="header">
  	<div class="header-left">
      <span class="iconfont">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
       输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
      
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
   </router-link>
  </div>
</template>

<script>
export default {
  name:'HomeHeader',
  props: {
    city: String
  }
}

</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
	.header {
		height: 0.86rem;
    line-height: 0.86rem;
		background: $bgColor;
    font-size:0.28rem;
    color: #fff;
	  }
  .header-left {width: 0.64rem; float: left}
  .header-left span {display: block; text-align: center}
  .header-input {float: left;width: 65%;height: 0.64rem; line-height:0.64rem;
    color:#ccc;background: #fff; border-radius: 0.1rem;margin-top: .1rem; margin-left: 0.2rem; padding-left: 0.1rem}

  .header-right {width: 1.24rem; float: right; text-align: center}
  .header-right .arrow-icon {font-size: 0.2rem}
</style>
