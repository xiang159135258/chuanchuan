<template>
    <div>
        <div class="sreach">
            <input v-model="keyword" type="text" class="sreach-input" placeholder="输入城市名字或者拼音">
        </div>
        <div class="sreach-content" ref="sreach" v-show="keyword">
            <ul>
                <li class="sreach-item border-bottom" v-for="item of list" :key="item.name" @click="handleCityChange(item.name)">
                    {{ item.name }}
                </li>
                <li class="sreach-item border-bottom" v-show="hasNoData">
                    无法找到匹配项
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
    name: 'CitySreach',
    props : {
        cities : Object
    },
    data () {
        return {
            keyword : '',
            list : [],
            timer : null
        }
    },
    methods: {
        handleCityChange (city) {
            // 有mapMutations 之后可以不是用下列调用方式
            // this.$store.dispatch('ChangeCity', city)
            this.ChangeCity(city)
            this.$router.push('/')
        },
        ...mapMutations(['ChangeCity'])
    },
    computed : {
        hasNoData () {
            return !this.list.length
        }
    },
    watch : {
        keyword () {
            if (this.timer) {
                clearTimeout (this.timer)
            }
            if (!this.keyword) {
                this.list = []
                return
            }
            this.timer = setTimeout(() => {
                const result = []
                for (let i in this.cities) {
                    this.cities[i].forEach((value) => {
                        if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1){
                            result.push(value)
                        }
                    });
                }
            this.list = result
            }, 100)

        }
    },
    mounted () {
        this.scroll  = new Bscroll(this.$refs.sreach)
    },
}
</script>

<style lang="stylus" scoped>

    @import '~styles/varibles.styl';

    .sreach
        height: 36px
        padding: 0 5px
        background-color $bgColor
        .sreach-input
            box-sizing: border-box
            width: 100%
            height 32px
            padding: 0 5px
            line-height: 32px
            text-align: center
            border-radius: 3px
            color #666
            outline: none
            border: none
    
    .sreach-content
        overflow: hidden
        position: absolute
        z-index: 1
        top 79px
        left: 0
        right: 0
        bottom: 0
        background-color #eee
        .sreach-item
            background-color #fff
            line-height: 31px
            padding-left: 10px
            color: #665
</style>