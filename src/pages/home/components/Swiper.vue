<template>
<div class="wrapper">
  <swiper :options="swiperOption" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="item of list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl" alt="">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        initialSlide: 0,
        speed: 400,
        autoplay: 2000,
        autoplayDisableOnInteraction: false,
        observer: true, // 修改swiper自己或子元素时，自动初始化swiper
        observeParents: true // 修改swiper的父元素时，自动初始化swiper
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="scss">
// 样式穿透，不受scoped限制
.swiper-pagination-bullet-active{
  background: #fff !important;
}
</style>

<style lang="scss" scoped>
.wrapper {
  width: 100%;
  height: 0;
  overflow: hidden;
  padding-bottom: 48.8%;
  background: #eee;
  .swiper-img {
    width: 100%;
  }
}

</style>
