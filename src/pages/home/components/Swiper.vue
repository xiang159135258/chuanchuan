<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <swiper-slide v-for="item of list" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl" >
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
    
</template>

<script>
export default{
    name: 'HomeSwiper',
    props: {
        list: Array
    },
    data (){
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                loop: true
            }
            
        }
    },
    computed: {
        showSwiper () {
            return this.list.length
        }
    }
}
</script>

<!-- >>> ： 表示穿透，使该样式的适用范围不局限在该组件 -->
<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
        background-color: #fff
    .wrapper
        overflow: hidden
        width: 100%     
        background-color: #eee
    .swiper-img
        width: 100%
        height: 150px
</style>