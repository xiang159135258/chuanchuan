<template>
    <div class="header">
        <router-link to="/">
            <div class="header-back">
                <span class="iconfont icon-fanhui"></span>
            </div>
        </router-link>
        城市选择
    </div>
</template>

<script>
export default {
    name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>

    @import '~styles/varibles.styl';

    .header
        position: relative
        overflow: hidden
        height : $headerHight
        line-height: $headerHight
        text-align: center
        color: #fff
        background :$bgColor
        font-size: 16px
        .header-back
            position absolute
            width: 32px
            text-align: center
            font-size: 20px
            color: #fff
</style>