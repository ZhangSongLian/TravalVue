<template>
    <ul  class="list">
        <li class="item" 
        v-for="(item,key) of cities" 
        :key="key" 
        @click="handleLetterClick"
        >
            {{key}}
        </li>
    </ul>
    
</template>

<script>
export default {
    name:'CityAlphabet',
    props: {
        cities:Object
    },
    methods: {
        handleLetterClick (e) {
            this.$emit('change', e.target.innerText)   //通过$emit向父组件传递数据 父组件再监听该事件
            // console.log(e.target.innerText)
        }
    }
}
</script>

<style lang="stylus" scoped>
.list{
    display flex;
    flex-direction column;
    justify-content center;
    position fixed;
    top 1.88rem;
    right 0;
    bottom 0;
    width: .3rem;
    text-transform: uppercase;
    z-index:99;
    
}
.item {
    line-height: 0.4rem;
    text-align: center;
     color: #555;
     font-size 0.23rem;
}
</style>


