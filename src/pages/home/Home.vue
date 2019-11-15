<template>
    <div>
         <!-- 父组件通过props方式向子组件传递数据 -->
        <home-header :city="city"></home-header>
        <home-swiper v-bind:list="swiperList"></home-swiper>
        <home-icons  v-bind:list="iconList"></home-icons>
        <home-recommend v-bind:recommendList="recommendList"></home-recommend>
        <home-weekend></home-weekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios' 


export default {
    name:"Home",
    components: {
        HomeHeader:HomeHeader,
        HomeSwiper:HomeSwiper,
        HomeIcons:HomeIcons,
        HomeRecommend:HomeRecommend,
        HomeWeekend:HomeWeekend
    },
    data (){
        return {
            city:"",
            swiperList:[],
            iconList:[],
            recommendList:[]
        }
    },
    methods: {
        getHomeInfo () {
           axios.get('/api/index.json')
                .then(this.getHomeInfoSucc)
        },
        getHomeInfoSucc (res) {
            res = res.data
             if (res.ret && res) {
                 this.city = res.city
                 this.swiperList = res.swiperList
                 this.iconList = res.iconList
                 this.recommendList = res.recommendList
             }
        }
    },
    // mounted 编译好的html挂载到页面完成后执行的事件钩子，此钩子函数中一般会做一些ajax请求获取数据进行数据初始化
    mounted () {
        this.getHomeInfo ()
    },
}
</script>

<style>

</style>

