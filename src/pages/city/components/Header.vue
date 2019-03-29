<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="header-left"><div class="iconfont header-back">&#xe624;</div></div>
    </router-link>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'CityHeader',
  data () {
    return {

    }
  },
  components: {

  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
@import '~@/assets/styles/varibles.scss';
.header {
  height: 88px;
  overflow: hidden;
  line-height: 88px;
  text-align: center;
  color: #fff;
  background: $bgColor;
  font-size: 28px;
  position: relative;
  .header-left {
    width: 80px;
    color: #fff;
    @include flex(row, inline-flex);
    height: 88px;
    position: absolute;
    top: 0;
    left: 0;
    justify-content: center;
    .header-back {
      font-size: 30px;
    }
  }
}
</style>
