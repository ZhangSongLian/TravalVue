<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
           <swiper :options="swiperOption">
                <swiper-slide v-for="(item,index) of imgs" :key="index">
                    <img class="swiper-img" :src="item" alt=""/>
                </swiper-slide>
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
export default {
    name:'CommonGallary',
      methods :{
        handleGallaryClick () {
            this.$emit('close')  //子组件向父组件传值 通过$emit方法
        }
    },
    props:{
        imgs: {
            type:Array,
            default() {
                return ['http://img1.qunarzz.com/sight/p0/1707/f4/f44d291b76de7b14a3.img.jpg_600x330_b3db0db7.jpg',
                'http://img1.qunarzz.com/sight/p0/1707/b9/b93e947051180ec5a3.img.jpg_r_800x800_dfbf15eb.jpg']
            }
        }
    },
    data:function(){
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
          paginationType : 'fraction',
          observer:true,
          observeParents:true
        }
      }
    }
  
}
</script>

<style lang="stylus" scoped>
    .container >>>.swiper-container {
        overflow:inherit
    }
    .container
        display:flex
        flex-direction:column
        justify-content:center
        position: fixed
        left:0
        right:0
        top:0
        bottom:0
        background:#000
        .wrapper 
         height:0
         width 100%
         padding-bottom:100%
         .swiper-img {
             width 100% 
         }
        .swiper-pagination{
            color:#fff;
            bottom:-1rem;
        }
</style>

