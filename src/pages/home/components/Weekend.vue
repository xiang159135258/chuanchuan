<template>
    <div>
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item border-bottom" v-for="item of list" :key="item.id">
                <div class="item-img-warpper">
                    <img class="item-img" :src="item.imgUrl" alt="">
                </div>
                
                <div class="item-info">
                    <p class="item-title">{{ item.title }}</p>
                    <p class="item-desc">{{ item.desc }}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'HomeWeekend',
    props: {
        list: Array
    }
}
</script>

<style lang="stylus" scoped>

    @import '~styles/mixins.styl';

    .title
        padding-left: 10px
        line-height: 40px
        background: #eee
        text-align: 10px
    .item-img-warpper
        height: 0
        overflow: hidden
        padding-bottom: 37.09%
        .item-img
            width: 100%
            height :150px

    .item-info
        padding: 5px
        .item-title
            line-height: 27px
            font-size: 16px
            ellipsis()
        .item-desc
            line-height: 20px
            color: #ccc
            ellipsis()
</style>