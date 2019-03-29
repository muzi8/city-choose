<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <!-- slides -->
        <swiper-slide v-for="(item, index) in imgs" :key="index">
          <img class="gallary-img" :src="item" alt="">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="scss">
.container {
  .swiper-container {
    overflow: inherit;
  }
}
</style>

<style lang="scss" scoped>
@import '../../assets/styles/layout.scss';

.container {
  @include flex(column, flex);
  justify-content: center;
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  z-index: 99;
  background: #000;
  .wrapper {
    width: 100%;
    height: 0;
    padding-bottom: 100%;
    .gallary-img {
      width: 100%;
    }
    .swiper-pagination {
      color: #fff;
      bottom: -100px;
    }
  }
}
</style>
