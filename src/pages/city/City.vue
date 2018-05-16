<template>
  <div>
      <city-header></city-header>
  </div>
</template>

<script>
    import axios from 'axios'
    import CityHeader from './components/Header'
    export default {
        name: 'City',
        components: {
            CityHeader
        },
        data () {
            return {
                cities: {},
                hotCities: [],
                letter: ''
            }
        },
        mounted () {
            this.getCityInfo()
        },
        methods: {
            getCityInfo () {
                axios.get('/api/city.json')
                    .then(this.handleGetCityInfoSucc)
            },
            handleGetCityInfoSucc (res) {
                res = res.data
                if (res.ret && res.data) {
                    const data = res.data
                    this.cities = data.cities
                    this.hotCities = data.hotCities
                }
            },
            handleLetterChange (letter) {
                this.letter = letter
            }
        }
    }
</script>

<style lang="stylus" scoped>

</style>
