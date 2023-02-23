<template>
    <div>
        <div class="title">热销推荐</div>
        <ul>
            <router-link
                tag="li"
                class="item border-bottom"
                v-for="item of list" 
                :key="item.id"
                :to="/detail/ + item.id"
                >
                <img class="item-img" :src="item.imgUrl" alt="">
                <div class="item-info">
                    <p class="item-title">{{ item.title }}</p>
                    <p class="item-desc">{{ item.desc }}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </router-link>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'HomeRecommmend',
    props : {
        list: Array
    }
}
</script>

<style lang="stylus" scoped>

    @import '~styles/mixins.styl';

    .title
        margin-top: 10px
        padding-left: 10px
        line-height: 40px
        background: #eee
        text-align: 10px
    .item
        overflow: hidden
        display: flex
        height: 95px
        .item-img
            width: 85px
            height: 85px
            padding: 5px
        .item-info
            flex: 1
            padding: 5px
            min-width: 0
            .item-title
                line-height: 27px
                font-size: 16px
                ellipsis()
            .item-desc
                line-height: 20px
                color: #ccc
                ellipsis()
            .item-button
                background: #ff9300
                line-height: 22px
                margin-top: 8px
                padding: 0 10px
                border-radius: 3px
</style>