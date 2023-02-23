<template>
    <div>   
        <router-link
        tag="div" 
        to="/" 
        class="header-abs"
        v-show="showAbs">
            <span class="iconfont icon-fanhui"></span>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
                <span class="iconfont icon-fanhui"></span>               
            </router-link>    
            
            景点详情   
        </div>
    </div>
</template>

<script>
export default {
    name: 'DetailHeader',
    data () {
        return {
            showAbs : true,
            opacityStyle: {
                opacity:0
            }
        }
    },
    methods : {
        handleScroll () {
            const top = document.documentElement.scrollTop
            // console.log(top) 
            if (top > 50) {
                let opacity = top /140
                opacity = opacity > 1 ? 1 : opacity
                this.opacityStyle = { opacity }
                this.showAbs = false
            } else {
                this.showAbs = true
            }
        }
    },
    activated () {
       window.addEventListener('scroll', this.handleScroll)
    },
    deactivated() {
        window.removeEventListener('scroll', this.handleScroll)
    },
}
</script>

<style lang="stylus" scoped>

    @import '~styles/varibles.styl';

    .header-abs
        position : absolute
        left: 10px
        top: 10px
        width 40px
        height 40px
        border-radius: 10px
        line-height: 40px
        text-align: center
        background rgba(3a, 3a, 3a, .8)
        .icon-fanhui
            font-size: 20px
            color: #fff
    
    .header-fixed
        z-index: 2
        position : fixed
        top: 0
        left :0
        right:0
        height : $headerHight
        line-height: $headerHight
        text-align: center
        color: #fff
        background :$bgColor
        font-size: 16px
        .icon-fanhui
            position absolute
            top: 2px
            left: 10px
            width: 32px
            text-align: center
            font-size: 20px
            color: #ccc
</style>
