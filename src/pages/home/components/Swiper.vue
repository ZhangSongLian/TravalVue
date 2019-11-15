<template>
  <div class="wrapper">
    <!-- v-if(判断是否隐藏)、v-for(把数据遍历出来)、v-bind(绑定属性) -->
  <swiper :options="swiperOption" v-if="showSwiper">
    <swiper-slide v-for="item of list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl" alt=""/>
    </swiper-slide>

    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeSwiper',
    props: {
        list:Array
    },
    data:function(){
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
          loop: true,
          autoplay: 3000,//可选选项，自动滑动
        }
      }
    },
    computed: {
      showSwiper (){
        return this.list.length
      }
    }
  }
</script>

<style lang="stylus" scoped>
  /*>>> 改变第三方插件swiper的样式*/
  .wrapper >>>.swiper-pagination-bullet-active {
    background: #fff !important;
  }
  .wrapper {
    overflow: hidden;
    width: 100%;
    height: 0;
    background: #eee;
    padding-bottom: 26.25%;
  }
  .swiper-img {
    width: 100%;
  }
</style>
