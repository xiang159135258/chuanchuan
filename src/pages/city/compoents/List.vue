<template>
    <div>
        <div class="list" ref="wrappers">
            <div>
                <div class="area"> 
                    <div class="title border-topbottom">当前城市</div>
                    <div class="button-list">
                        <div class="button-wrapper">
                            <div class="button">
                                {{ this.currentCity }}
                            </div>   
                        </div>
                    </div>
                </div>
                
                <div class="area"> 
                    <div class="title border-topbottom">热门城市</div>
                    <div class="button-list" >
                        <div class="button-wrapper" 
                            v-for="item of hot" 
                            :key="item.id"
                            @click="handleCityChange(item.name)"
                            >
                            <div class="button">{{ item.name }}</div>
                        </div>
                    </div>
                </div>
                
                <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
                    <div class="title border-topbottom">{{ key }}</div>
                    <div class="item-list">
                    <div
                        class="item border-bottom"
                        v-for="innerItem of item"
                        :key="innerItem.name"
                        @click="handleCityChange(innerItem.name)"
                    >
                        {{ innerItem.name }}
                    </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
    props: {
        hot: Array,
        cities: Object,
        letter: String
    },
    name: 'CityList',
    computed : {
        ...mapState({
            currentCity : 'city'
        })
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
    mounted () {
        this.scroll  = new Bscroll(this.$refs.wrappers)
    },
    watch : {
        letter() {
            if (this.letter) {
                const element = this.$refs[this.letter][0]
                this.scroll.scrollToElement(element)
            }
        }
    }
}
</script>

<style lang="stylus" scoped>

    @import '~styles/varibles.styl';

    .border-topbottom
        &:before
            border-color: #ccc
        &:after
            border-color: #ccc 

    .border-bottom
        &:before
            border-color: #ccc

    .list
        overflow: hidden;
        position: absolute;
        top: 79px;
        left: 0;
        right: 0;
        bottom: 0;
        
        .title
            line-height: 22px 
            background: #eee
            padding-left 5px
            color: #666
            font-size: 13px

        .button-list
            overflow hidden
            .button-wrapper
                float: left
                width: 33%
                .button
                    margin: 5px
                    padding: 5px 0
                    text-align: center
                    border: 2px solid #ccc
        .item-list {
            .item {
                margin: 5px
                padding: 5px
                line-height: 14px;
                padding-left: 5px;
            }
            }

</style>