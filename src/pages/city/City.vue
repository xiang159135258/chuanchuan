<template>
    <div>
        <CityHeader></CityHeader>
        <CitySreach :cities="cities"></CitySreach>
        <CityList :cities="cities" :hot="hotCities" :letter="letter"></CityList>
        <CityAlphabet :cities="cities" @change="handleLetterChange"></CityAlphabet>
    </div>
    
</template>

<script>
import CityHeader from './compoents/Header'
import CitySreach from './compoents/Sreach'
import CityList from './compoents/List'
import CityAlphabet from './compoents/Alphabet'
import axios from 'axios'


export default {
    name: 'City',
    components: {
        CityHeader,
        CitySreach,
        CityList,
        CityAlphabet,
    },
    data () {
        return {
            cities: {},
            hotCities: [],
            letter: ''
        }
    },

    methods: {
        getCityInfo () {
            axios.get('/api/city.json').then(this.getCityInfoSucc)
        },
        getCityInfoSucc (res) {
            console.log(res)
            res = res.data
            if (res.ret && res.data){
                const data = res.data
                this.cities = data.cities
                this.hotCities = data.hotCities
            }
        },
        handleLetterChange (letter) {
            this.letter = letter
        }
    },
    mounted () { 
        this.getCityInfo()
    }
}
</script>

<style lang="stylus" scoped>
 
</style>