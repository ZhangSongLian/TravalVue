<template>
    <div>
        <div>
             <!-- v-model  进行双向数据绑定 -->
            <input type="text" placeholder="输入城市名或拼音" class="search-ipt" v-model="keyworld">
        </div>
        <!-- 城市搜索功能 -->
        <div class="search-content" ref="search"  v-show="keyworld"><!--v-show="keyworld" 有值的时候显示  -->
            <ul>
                <li v-for="item of list" :key="item.id" class="search-item">{{item.name}}</li>
                <li class="search-item" v-show="hasNoDate">没有找到匹配数据</li> 
            </ul>
        </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'  //借助BScroll实现代码的滚动
export default {
  name:'CitySearch',
  props:{
      cities:Object //search 组件必须接受到city组件的数据cities
  },
  data () {
      return {
          keyworld:'',
          list:[],
          timer:null
      }
  },
  computed: { 
      hasNoDate() {
          return !this.list.length
      }
  },
   mounted(){
       this.scroll = new BScroll(this.$refs.search)
    },
  watch: { //监听keyworldde改变
      keyworld () {
          if (this.timer){
              clearTimeout(this.timer)
          }

          if (!this.keyworld) {
            this.list=[]
            return
          }
          this.timer = setTimeout(()=> {
               const result = []
            // 循环cities的内容
            for (let i in this.cities){
                this.cities[i].forEach((value) => { //将cities里的键值对abcd再循序一遍
                    if (value.spell.indexOf(this.keyworld) > -1 ||
                    value.name.indexOf(this.keyworld) > -1){
                        result.push(value)
                    }
                });
            }
            this.list = result
          },100)
      }
  }
}
</script>

<style lang="stylus" scoped>
    @import '../../../assets/styles/varibles.styl';
    .search {
        overflow: hidden;
        font-size: .14rem;
        line-height: .75rem;
        text-align: center;
        background: $bgColor;
        padding: .1rem;
        border-bottom: 1px solid #dbe1e4;
    }
    .search-ipt {
       box-sizing border-box;
       width 100%;
       height 0.62rem;
       line-height 0.62rem;
       border: 1px solid #dbe1e4;
       padding 0.1rem;
       text-align center;
       border-radius 0.06rem;
    }
    .search-content {
        overflow:hidden;
        position absolute;
        top:1.75rem;
        left: 0;
        right: 0;
        bottom: 0;
        z-index:999;
    }
    .search-item {
        line-height: .62rem;
        padding-left .2rem;
        background #fff;
       border-bottom:0.02rem solid #eee;
        color: #666;
    }
</style>


