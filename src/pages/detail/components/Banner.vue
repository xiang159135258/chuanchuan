<template>
    <div>
        <div class="banner" @click="handBannerClick">
            <img class="banner-img" src="https://imgs.qunarzz.com/sight/p0/2301/2b/2b1330228fd3ae11a3.water.jpg_710x360_2714081f.jpg" alt="" >
            <div class="banner-info">
                <div class="banner-title">北京环球度假区</div>
                <div class="banner-number">
                    <span class="iconfont icon-icon-test2"></span>
                    35
                </div>
            </div>
        </div>
        <CommonGallary 
        :imgs="imgs" 
        v-show="showGallary" 
        @close="handleGallaryClose"
        ></CommonGallary>
    </div>
</template>

<script>
import CommonGallary  from 'common/gallary/Gallary'
export default {
    name: 'DetailBanner',
    data () {
        return {
            showGallary: false,
            imgs : ["https://imgs.qunarzz.com/sight/p0/2301/14/14a72fe1b49dfc36a3.water.jpg_710x360_03da7434.jpg","https://imgs.qunarzz.com/sight/p0/2301/49/499955bd472067c7a3.water.jpg_1190x550_5a69675c.jpg"]
        }    
    },
    methods: {
        handBannerClick () {
            this.showGallary = true 
        },
        handleGallaryClose () {
            this.showGallary = false
        }
    },
    components: {
        CommonGallary
    }
}
</script>

<style lang="stylus" scoped>
    .banner
        position relative
        overflow: hidden
        height: 0
        padding-bottom: 50%
        .banner-img
            width: 100%
            object-fit: cover
        .banner-info
            display: flex
            position absolute
            left: 0
            right : 0
            bottom: 0
            line-height: 20px
            color #fff
            background-image: linear-gradient(top , rgba(0, 0, 0, 0), rgba(0,0,0,.8))
            .banner-title
                flex: 1
                padding 0 10px
                font-size: 16px
            .banner-number
                padding 0 10px
                height: 20px
                line-height: 20px
                border-radius: 10px
                background: rgba(0,0,0,.8)
</style>