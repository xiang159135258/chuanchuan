<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont icon-fanhui"></span>
        </div>
        <div class="header-input">
            <span class="iconfont icon-icon-test"></span>
            输入景点/游玩主题
        </div>
        <router-link to="/city">
            <div class="header-right">
                    {{ this.city }}
                <span class="iconfont icon-icon-test1"></span>
            </div>
        </router-link>

        
    </div>
</template>

<script>
import { mapState } from 'vuex';
export default {
    name: 'Home',
    computed : {
        ...mapState(['city'])
    }
}
</script>

<!-- lang="stylus"  調用stylus 这个库-->
<!-- scoped ： 指定样式只对该组件有效，不影响其他组件的样式 -->
<!-- 1rem = html font-size = 50px -->
<style lang="stylus" scoped>

    @import '~styles/varibles.styl';
    @import '~styles/mixins.styl';

    .header
        display: flex
        line-height : $headerHight
        background: $bgColor
        color: #fff 
        .header-left
            width : 32px
            float: left 
            .icon-fanhui
                margin-left: 8px

        .header-input
            flex: 1
            line-height 32px
            height 32px
            margin-top: 6px
            margin-left: 2px
            background: #fff
            border-radius: 5px
            color: #ccc
            .icon-icon-test
                margin-left: 5px

        .header-right
            font-size: 14px
            min-width: 62px
            float: right
            text-align: center
            color: #fff
            ellipsis()
            .icon-icon-test1
                padding-top: 8px
</style>

