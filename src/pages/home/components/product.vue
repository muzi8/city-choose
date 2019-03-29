<template>
  <div class="productWrapper">
    <div
    class="item"
    v-for="item of list"
    :key="item.id"
    :to="'/detail/' + item.id">
      <img :src="item.img" alt="">
      <div class="dec">
        <p class="title">{{item.title}}</p>
        <p>
          <span class="price">{{item.price | formatMoney}}</span>
          <span class="saleNum">销量{{item.saleNum}}件</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'HomeProduct',
  props: {
    list: Array
  },
  filters: {
    formatMoney: function (value) {
      return '¥' + value
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../../../assets/styles/layout.scss';
.productWrapper {
  .item {
    @include flex(row, inline-flex);
    width: 50%;
    height: 540px;
    box-sizing: border-box;
    padding: 40px 30px;
    cursor: pointer;
    border-bottom: 1px solid #eee;
    &:nth-child(2n+1) {
      border-right: 1px solid #eee;
    }
    img {
      width: 100%;
      height: 300px;
    }
    .title {
      margin: 20px 0 36px;
      color: $font555;
      font-size: 24px;
      height: 50px;
      @include twoEllipsis();
    }
    .price {
      color: $productPrice;
      font-size: 26px;
      margin-right: 20px;
    }
    .saleNum {
      color: $font555;
      font-size: 20px;
    }
  }
}
</style>
