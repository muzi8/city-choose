<template>
<div>
  <home-header></home-header>
  <home-swiper :list = "swiperList"></home-swiper>
  <home-icons :list = "iconsList"></home-icons>
  <home-recommend></home-recommend>
  <home-product :list = "productList"></home-product>
</div>
</template>

<script type="text/ecmascript-6">
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/recommend'
import HomeProduct from './components/product'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeProduct
  },
  data () {
    return {
      lastCity: '',
      swiperList: [],
      iconsList: [],
      productList: []
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
        const data = res.data
        this.swiperList = data.swiperList
        this.iconsList = data.iconsList
        this.productList = data.productList
      }
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style scope>

</style>
