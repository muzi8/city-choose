<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.text">
          <router-link :to="item.href">
            <img class="icon-img" :src="item.src" alt="">
          <p>{{item.text}}</p>
          </router-link>
        </div>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../../assets/styles/layout.scss";
.icons >>> .swiper-container {
  width: 100%;
  box-sizing: border-box;
  padding: 50px 0;
}

.icons {
  @include flex(row, flex);
  width: 100%;
  height: 394px;
  box-sizing: border-box;
  border-bottom: 4px solid $bgF5;
  .icon {
    @include flex(column, inline-flex);
    width: 25%;
    &:nth-child(1),
    &:nth-child(2),
    &:nth-child(3),
    &:nth-child(4) {
      margin-bottom: 28px;
    }
    a {
      @include flex(column, inline-flex);
      justify-content: center;
      align-items: center;
      width: 100%;
      .icon-img {
        width: 97px;
        height: 97px;
        margin-bottom: 10px;
      }
      p {
        font-size: 24px;
        color: $font333;
        width: 100%;
        text-align: center;
        @include textEllipsis();
      }
    }
  }
}
</style>
<style lang="scss">
.icons {
  .swiper-pagination-bullet {
    background: #007aff !important;
  }
}
</style>
