<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
       <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>  <!-- 城市列表 -->
        <city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
    </div>
</template>

<script>

import axios from 'axios' 
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'


export default {
    name:'City',
    components: {
        CityHeader:CityHeader,
        CitySearch:CitySearch,
        CityList:CityList,
        CityAlphabet:CityAlphabet
    },
    data () {
        return {
            cities:{},
            hotCities:[],
            letter:""
        }
    },
     methods: {
        getHomeInfo () {  //https://www.kancloud.cn/yunye/axios/234845
           axios.get('/api/city.json')   //axios是一个基于promise的HTTP库，可以用在浏览器和node.js中
                .then(this.getHomeInfoSucc)
        },
        getHomeInfoSucc (res) {
           res = res.data
           if(res.ret && res.data){
             const data = res.data
             this.cities = data.cities
             this.hotCities = data.hotCities
           }
        },
        handleLetterChange (letter) {
            this.letter = letter
            console.log(letter)
        }
    },
    mounted () {
        this.getHomeInfo ()
    },
}
</script>

<style>

</style>
