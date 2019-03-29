<template>
  <div class="page">
    <detail-banner
    :sightName="sightName"
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs"></detail-banner>
    <detail-header ></detail-header>
    <detail-list :list="list"></detail-list>
    <div class="content"></div>
  </div>
</template>

<script type="text/ecmascript-6">
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      list: [],
      sightName: '',
      bannerImg: '',
      gallaryImgs: []
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style lang="scss" scoped>
.content {
  height: 1000px;
}
</style>
