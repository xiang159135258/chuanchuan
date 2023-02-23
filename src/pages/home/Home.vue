<template>
    <div>
        <HomeHeader></HomeHeader>
        <HomeSwiper :list="swiperList"></HomeSwiper>
        <HomeIcons :list="iconList"></HomeIcons>
        <HomeRecommmend :list="recommendList"></HomeRecommmend>
        <HomeWeekend :list="weekendList"></HomeWeekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header';
import HomeSwiper from './components/Swiper';
import HomeIcons from './components/Icons';
import HomeRecommmend from './components/Recommend';
import HomeWeekend from './components/Weekend';
import axios from 'axios'
import { mapState } from 'vuex'
export default {
    name: 'Home',
    components:{
        HomeHeader,
        HomeSwiper,
        HomeIcons,
        HomeRecommmend,
        HomeWeekend,
    },
    data () {
        return {
            lastCity : '',
            swiperList : [],
            iconList : [],
            recommendList : [],
            weekendList : []
        }
    },
    computed : {
        ...mapState(['city'])
    },
    methods: {
        getHomeInfo () {
            axios.get('/api/index.json?city=' + this.city).then(this.getHomeInfoSucc)
        },
        getHomeInfoSucc (res) {
            console.log(res)
            res = res.data
            if (res.ret && res.data){
                const data = res.data
                this.swiperList = data.swiperList
                this.iconList = data.iconList
                this.recommendList = data.recommendList
                this.weekendList = data.weekendList
            }
        }
    },
    mounted () {
        this.lastCity = this.city
        this.getHomeInfo()
    },
    activated () {
        if (this.lastCity !== this.city) {
            this.lastCity = this.city
            this.getHomeInfo()
        }
    }
}
</script>

<style>
    .home {
        font-size: 50px;
        font-style: initial;
    }
</style>
