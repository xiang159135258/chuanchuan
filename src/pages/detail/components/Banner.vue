<template>
    <div>
        <div class="banner" @click="handBannerClick">
            <img class="banner-img" :src="bannerImg" alt="" >
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div class="banner-number">
                    <span class="iconfont icon-icon-test2"></span>
                    {{ this.galleryImgs.length }}
                </div>
            </div>
        </div>
        <FadeAnimation>
            <CommonGallary 
            :imgs="galleryImgs" 
            v-show="showGallary" 
            @close="handleGallaryClose"
            ></CommonGallary>
        </FadeAnimation>
       
    </div>
</template>

<script>
import CommonGallary  from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
    name: 'DetailBanner',
    props: {
        sightName: String,
        bannerImg: String,
        galleryImgs: Array
    },
    data () {
        return {
            showGallary: false,
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
        CommonGallary,
        FadeAnimation
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