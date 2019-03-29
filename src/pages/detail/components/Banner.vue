<template>
<div>
  <div class="banner" @click="handleBannerClick">
    <img class="banner-img" :src="bannerImg" alt="">
    <div class="banner-info">
      <div class="banner-title">{{this.sightName}}</div>
      <div class="banner-number"><span class="iconfont banner-icon">&#xe626;</span>{{this.bannerImgs.length}}</div>
    </div>
  </div>
  <fade-animation>
    <common-gallary
    :imgs="bannerImgs"
    v-show="showGallary"
    @close="handleGallaryClose"></common-gallary>
  </fade-animation>
</div>
</template>

<script type="text/ecmascript-6">
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../../../assets/styles/layout.scss';
@import '../../../assets/styles/varibles.scss';
.banner {
  overflow: hidden;
  height: 0;
  padding-bottom: 60%;
  position: relative;
  .banner-img {
    width: 100%;
  }
  .banner-info {
    @include flex(row, flex);
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 60px;
    color: #fff;
    align-items: center;
    background-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0, 0, 0, 0)), to(rgba(0, 0, 0, 0.8)));
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));
    .banner-title {
      @include twoEllipsis();
      flex: 1;
      font-size: 32px;
      padding: 0 20px;
    }
    .banner-number {
      height: 32px;
      padding: 0 40px;
      line-height: 32px;
      border-radius: 20px;
      background: rgba(0, 0, 0, .8);
      font-size: 22px;
      .banner-icon {
        font-size: 24px;
        margin-right: 10px;
      }
    }
  }
}
</style>
