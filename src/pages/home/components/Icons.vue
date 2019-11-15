<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div class="iconlist" v-for="list of page" :key="list.id">
          <div class="icon-img">
            <img :src="list.iconImg" alt="">
          </div>
          <p class="icon-desc">{{list.iconDesc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>

    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeIcons',
    props:{
       list:Array
    },
    data:function () {
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
        },
        // iconList: [
        //   {
        //     id:"001",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
        //     iconDesc:'景点门票'
        //   },
        //   {
        //     id:"002",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
        //     iconDesc:'广州必游'
        //   },
        //   {
        //     id:"003",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png",
        //     iconDesc:'动植物园'
        //   },
        //   {
        //     id:"004",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png",
        //     iconDesc:'游乐场'
        //   },
        //   {
        //     id:"005",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/89/55083b0f1951f302.png",
        //     iconDesc:'游船游艇'
        //   },
        //   {
        //     id:"006",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png",
        //     iconDesc:'夏日玩水'
        //   },
        //   {
        //     id:"007",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png",
        //     iconDesc:'城市观光'
        //   },
        //   {
        //     id:"008",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png",
        //     iconDesc:'汽车票'
        //   },
        //   {
        //     id:"008",
        //     iconImg:"http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png",
        //     iconDesc:'汽车票'
        //   }

        // ]
      }
    },
    computed: { //计算属性
      pages:function () {
        const pages = []
        this.list.forEach((item,index) =>{
          const page = Math.floor(index / 8)
          if (!pages[page]) {
            pages[page] = []
          }
          pages[page].push(item)
        })
        return pages
      }
    }
  }
</script>

<style lang='stylus' scoped>
  /*引入mixins.styl文件样式*/
  @import '../../../assets/styles/mixins.styl';
  .icons {
      padding 0.1rem 0;
  }
  .icons >>> .swiper-container {
    overflow: hidden;
    height: 0;
    padding-bottom:  50%;
  }
  .iconlist {
    overflow: hidden;
    float: left;
    width: 25%;
    height: 1.5rem;
    font-size: 0.28rem;
    text-align: center;
    padding-top: .1rem;
    color: #333;
  }
  .icon-img {
    width: 1.12rem;
    height: 1.12rem;
    margin: 0 auto;
    margin-bottom: 0.1rem;
  }
  .icon-img img {
    width: 100%;
    height: 100%;
  }
  .icon-desc {
    /*调用mixins.styl文件的样式方法*/
    ellipse()
  }
</style>
