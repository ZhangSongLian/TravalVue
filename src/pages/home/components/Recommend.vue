<template>
  <div>
    <div class="title">热销推荐</div>
      <ul class="listul">
        <!-- 传参数 -->
        <router-link 
            tag="li"
            class="item" 
            v-for="item of recommendList" 
            :key="item.id"
            :to="'/detail/' + item.id"
          >
            <div class="item-img-wrapper">
              <img class="item-img" :src="item.imgUrl" alt="">
            </div>
            <div class="item-info">
              <p class="item-title">{{item.title}}</p>
              <p class="item-desc">{{item.desc}}</p>
              <button class="item-btn">查看详情</button>
            </div>
        </router-link>
      </ul>
  </div>
</template>

<script>
  export default {
    name: 'HomeRecommend',
     props: {
        recommendList:Array
    }
   
  }
</script>

<style lang='stylus' scoped>
  @import '~styles/mixins.styl';
    .title {
      line-height: .7rem;
      background: #eee;
      text-indent: .2rem;
    }
    .listul {
      margin-left: 0.24rem;
    }
    .item {
      overflow: hidden;
      display: flex;
      height: 1.9rem;
      padding: 0.2rem 0;
    }
    .item-img {
      width: 2rem;
      height: 100%;
    }
    .item-info {
      flex: 1;
      min-width: 0;
      padding:0.15rem;
    }
    .item-info .item-title {
      font-size: 0.32rem;
      line-height: 0.54rem;
      color: #000;
      ellipse()
    }
    .item-desc {
      line-height: 0.4rem;
      font-size: 0.28rem;
      color: #616161;
      padding-bottom: 0.15rem;
      ellipse()
    }
    .item-btn {
      background: #ff9300;
      padding: 0.065rem;
      border: none;
      border-radius: 0.06rem;
      color: #fff;
      font-size: 0.24rem;
      margin-top -0.2rem;
    }
</style>
