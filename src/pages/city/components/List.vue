<template>
    <div class="list" ref="wrapper">
        <div>
        <div class="area">
            <div class="title">当前城市</div>
            <div class="button-list">
                <div class="button-wraper">
                    <div class="button">北京</div>
                </div>
            </div>
        </div>
        <div class="area">
            <div class="title">热门城市</div>
            <div class="button-list">
                <div class="button-wraper" v-for="item of hot" v-bind:key="item.id">
                    <div class="button">{{item.name}}</div>
                </div>
            </div>
        </div>
        <div class="area"
         v-for="(item,key) of cities" 
         :key="key"
         :ref="key"
         >
            <div class="title">{{key}}</div>
            <div class="item-list">
                <div class="item" v-for="innerItem of item" :key="innerItem.id">{{innerItem.name}}</div>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
    name:'CityList',
    props:{
        hot:Array,
        cities:Object,
        letter:String
    },
    mounted(){
       this.scroll = new BScroll(this.$refs.wrapper)
    },
    watch: { //监听器  点击字母跳到相应的区域
        letter () {
            if(this.letter) {
                const element = this.$refs[this.letter][0]
                this.scroll.scrollToElement(element)
            }
            // console.log(this.letter)
        }
    }
}
</script>

<style lang="stylus" scoped>
     @import '../../../assets/styles/varibles.styl';
     .list {
         overflow hidden;
         position absolute;
         top 1.78rem;
         left 0;
         right 0;
         bottom 0;
        
     }
     .title {
         width 100%;
         height 0.54rem;
         line-height 0.54rem;
         background-color: #f2f8fb;
         border-bottom: 1px solid #d2d9df;
         padding-left 0.2rem;
         color #666;
         font-size 0.26rem;
     }
     .button-list {
        overflow hidden;
        padding 0.1rem 0.6rem 0.1rem 0.1rem;
     }
     .button-wraper {
        float left;
        width 33.33%;
     }
     .button {
         margin 0.1rem;
         text-align center;
         border:0.02rem solid #ccc;
         padding  0.1rem 0;
         border-radius 0.06rem;
     }
     
     .item {
         line-height 0.76rem;
         color #666;
         padding-left 0.2rem;
         border-bottom: 0.01rem solid #d2d9df;
     }
</style>


