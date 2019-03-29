<template>
  <div class="header">
    <div class="header-left"><div class="iconfont back-icon">&#xe624;</div></div>
    <div class="header-input"><span class="iconfont search-icon">&#xe632;</span> 请输入搜索内容</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script type="text/ecmascript-6">
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
.header {
  @include flex(row);
  width: 100%;
  height: 88px;
  background: $bgColor;
  align-items: center;
  color: #fff;
  .header-left {
    width: 80px;
    .back-icon {
      text-align: center;
      font-size: 30px;
    }
  }
  .header-input {
    @include flex(row, inline-flex);
    align-items: center;
    flex: 1;
    background: #fff;
    border-radius: 28px;
    height: 56px;
    text-indent: 20px;
    color: $colorheader;
    font-size: 28px;
    .search-icon {
      text-align: center;
      font-size: 34px;
      margin-right: 10px;
    }
  }
  .header-right {
    @include flex(row, inline-flex);
    min-width: 104px;
    padding: 0 10px;
    height: 88px;
    text-align: center;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    color: #fff;
    .arrow-icon {
      font-size: 20px;
      margin-left: 16px;
    }
  }
}
</style>
