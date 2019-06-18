<template>
    <div>
        <!-- <home-header :city="city"></home-header> -->
        <home-header></home-header>
        <home-swiper :list="swiperList"></home-swiper>
        <home-icons :list="iconList"></home-icons>
        <home-recommend :list="recommendList"></home-recommend>
        <home-weekend :list="weekendList"></home-weekend>
    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      // city: '',
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const resData = res.data
        // this.city = res.city
        this.swiperList = resData.swiperList
        this.iconList = resData.iconList
        this.recommendList = resData.recommendList
        this.weekendList = resData.weekendList
      }
      console.log(res)
    }
  },
  // mounted 是vue生命周期函数，在不使用缓存的情况下，每次生成页面调用，如果使用缓存后，只在第一次生成页面调用
  mounted () {
    // console.log('mounted')
    this.lastCity = this.city
    this.getHomeInfo()
  },
  // activated 是使用keep-alive组件后，vue才有的生命周期函数，每次生成页面前调用
  activated () {
    // console.log('activated')
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style>

</style>
