<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="list of weekendList" :key="list.id">
        <div class="item-img-wrapper">
          <img class="item-img" :src="list.imgUrl" alt="">
        </div>
        <div class="item-info">
          <p class="item-title">{{list.title}}</p>
          <p class="item-desc">{{list.desc}}</p>
        </div>
      </li>
    </ul>

  </div>

</template>

<script>
  export default {
    name: 'HomeWeekend',
    data:function () {
      return {
        weekendList:[
          {
            id:'001',
            imgUrl:'http://img1.qunarzz.com/sight/source/1505/92/580e9ea4f37a1b.jpg_r_640x214_72112761.jpg',
            title:'广州必游TOP10',
            desc:'感受现代与传统相融合的广州'
          },
          {
            id:'002',
            imgUrl:'http://img1.qunarzz.com/sight/source/1506/fd/08f524fa9455b4.jpg_r_640x214_b37dbb39.jpg',
            title:'暑期玩转粤港澳',
            desc:'来广州来长隆，就对了，就够了~'
          },
          {
            id:'003',
            imgUrl:'http://img1.qunarzz.com/sight/source/1606/88/56f7f4bd0493fe.jpg_r_640x214_f8c0994a.jpg',
            title:'签到广州长隆',
            desc:'感受现代与传统相融合的广州'
          }
        ]
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import '../../../assets/styles/mixins.styl';
  .title {
    line-height: .7rem;
    background: #eee;
    text-indent: .2rem;
  }
  .item-img-wrapper {
    overflow: hidden;
    height: 0;
    padding-bottom: 37.4375%;
  }
  .item-img-wrapper img {
    width: 100%;
  }
  .item-info {
    padding:0.15rem;
  }
  .item-info .item-title {
    font-size: 0.32rem;
    line-height: 0.54rem;
  ellipse()
  }
  .item-desc {
    line-height: 0.4rem;
    font-size: 0.28rem;
    color: #616161;
    padding-bottom: 0.15rem;
  ellipse()
  }
</style>
