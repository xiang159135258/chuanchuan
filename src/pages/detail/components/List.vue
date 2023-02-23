<template>
    <div>
        <div class="item" v-for="item of list" :key="item.title">
            <div class="item-title">
                <span class="item-title-icon"></span>
                {{ item.title }}
            </div>
            <div class="item-children" v-if="item.children">
                <DetailList :list="item.children"></DetailList>
            </div>           
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'DetailList',
    props : {
        list : Array,
    },
   
}
</script>

<style lang="stylus" scoped>
    .item-title-icon
        position relative
        left: 2px
        top 10px
        display: inline-block
        width: 24px
        height 24px
        background :url(https://imgs.qunarzz.com/vs_ceph_vcimg/1a4c2d83b507b204486761c00f2bb21d.png) 0 -.45rem no-repeat;
        margin-right: 2px
        background-size : 24px 24px

    .item-title {
        line-height: 40px
        font-size: 16px
        padding: 0 10px 
    }
    .item-children
      padding: 0 10px
</style>