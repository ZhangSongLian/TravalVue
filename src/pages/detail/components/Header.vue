<template>
  <div ref="wrapper">
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <span class="iconfont header-abs-back" >&#xe624;</span>
    </router-link>
    <div 
      class="header-fixed"
      v-show="!showAbs"
      :style="opacityStyle"
     >
      <router-link tag="div" to="/">
        <span class="iconfont header-fixed-back" >&#xe624;</span>
      </router-link>
      景点详情
    </div>

  </div>
</template>

<script>

export default {
  name:'DetailHeader',
  data () {
    return {
      showAbs:true,
      opacityStyle: {
        opacity:0
      }
    }
  },
  methods:{
    handleScroll () {
      console.log(scroll)
      console.log(document.documentElement.scrollTop)
      var top = document.documentElement.scrollTop;
      if(top > 60) {
        let opacity = top/140
        // console.log(opacity)
        opacity = opacity>1?1:opacity //三目运算法
        this.opacityStyle = {
          opacity:opacity
        }
        this.showAbs = false
      }else{
        this.showAbs = true
      }
     
      }
  },
  //created:在模板渲染成html或者模板编译进路由前调用
  // mounted:在模板渲染成html后调用，通常是初始化页面完成后，再对html的dom节点进行一些需要的操作。
  mounted () { //页面一被展示就执行这个钩子
     window.addEventListener('scroll', this.handleScroll) //绑定scroll事件，一旦这个事件执行对应的handleScroll方法会被执行
  },
  // /activated()：在vue对象存活的情况下，进入当前存在activated()函数的页面时，一进入页面就触发；可用于初始化页面数据等
  // activated() {
  //    window.addEventListener('scroll', this.handleScroll) //绑定scroll事件，一旦这个事件执行对应的handleScroll方法会被执行
  // },
  // deactivated () {  
  //   window.removeEventListener('scroll',this.handleScroll) //对scroll这个全局事件进行解绑
  // }
  
 

}

</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .header-abs {
    position:absolute
    left:.2rem
    top:.2rem
    width:.8rem
    height: .8rem
    line-height: .8rem;
    text-align:center;
    border-radius: .4rem
    background: rgba(0, 0, 0,.7)
  }
  .header-abs-back {
    color: #fff
    font-size:0.4rem
  }

  .header-fixed{
    position: fixed
    top:0
    left:0
    right:0
    height 0.86rem;
    line-height 0.86rem;
    text-align center;
    color #fff;
    background $bgColor;
    z-index :9
   
  }
  .header-fixed-back {
    width 0.64rem;
    text-align center;
    font-size .35rem;
    color #fff;
    position absolute;
    left 0;
    top 0;
  }
    
</style>
