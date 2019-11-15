<template>
  <div>
     <div class="banner" @click="handleBannerClick">
         <img class="banner-img" 
      src="http://img1.qunarzz.com/sight/p0/1707/f4/f44d291b76de7b14a3.img.jpg_600x330_b3db0db7.jpg" alt="">
      <div class="info">
        <div class="title">大连圣亚海洋世界</div>
      </div>
    </div>
    
    <common-gallary :imgs="imgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>

  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name:'DetailBanner',
  data () {
     return{
        showGallary: false,
        imgs:['http://img1.qunarzz.com/sight/p0/1707/f4/f44d291b76de7b14a3.img.jpg_600x330_b3db0db7.jpg',
                'http://img1.qunarzz.com/sight/p0/1707/b9/b93e947051180ec5a3.img.jpg_r_800x800_dfbf15eb.jpg']
     }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
       this.showGallary = false
    }
  },
  components: {
        CommonGallary:CommonGallary,   
  }

}

</script>

<style lang="stylus" scoped>
    .banner {
      position relative;
      overflow: hidden
      height:0
      padding-bottom:55%
    }
    .banner-img{
      width:100%
    }   
    .info {
      width 100%;
      line-height 0.6rem
      position:absolute;
      left:0;
      bottom:0;
      background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8)) //从上往下渐变
    }
    .title {
      padding-left 0.1rem;
      color:#fff
    }

</style>
