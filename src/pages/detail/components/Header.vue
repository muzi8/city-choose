<template>
  <div>
    <router-link
    tag="div"
    to="/"
    class="header-abs"
    v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed"
    v-show="!showAbs"
    :style="opacityStyle">
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      商品详情
      </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  // activated () {
  //   window.addEventListener('scroll', this.handleScroll)
  // },
  // deactivated () {  // 外层用了keep-alive 的exclude 所以这里不再有这两个钩子函数
  //   window.removeEventListener('scroll', this.handleScroll)
  // },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop || document.body.scrollTop
      if (top >= 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
@import '~@/assets/styles/varibles.scss';
.header-abs {
  position: absolute;
  left: 20px;
  top: 20px;
  width: 60px;
  height: 60px;
  border-radius: 40px;
  text-align: center;
  line-height: 60px;
  background: rgba(0, 0, 0, .8);
  .header-abs-back {
    color: #fff;
    font-size: 30px;
  }
}
.header-fixed {
  z-index: 2;
  height: 80px;
  overflow: hidden;
  line-height: 80px;
  text-align: center;
  color: #fff;
  background: $bgColor;
  font-size: 28px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  a {
    @include flex(row, inline-flex);
    width: 80px;
    color: #fff;
    height: 80px;
    position: absolute;
    top: 0;
    left: 0;
    justify-content: center;
  }
  .header-fixed-back {
    font-size: 30px;
  }
}
</style>
