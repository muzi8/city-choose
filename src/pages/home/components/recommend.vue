<template>
<div class="recommend">
  <section class="recommend-content">
    <div class="item">
      <h4>不惧酷暑 美丽一夏</h4>
      <p>满199减30</p>
      <img src="//img.alicdn.com/bao/uploaded/i1/TB1bDybf5QnBKNjSZFmSuwApVXa.jpg_300x1000Q75s0.jpg_.webp" alt="">
    </div>
    <div class="item">
      <ul>
        <li>
          <img src="//gw.alicdn.com/bao/uploaded/i1/i1/1574983217/TB2MyhpaerAQeBjSZPcXXbJ6pXa_!!1574983217.png_360x360q75.jpg_.webp" alt="">
          <h4>0.01MM超薄体验</h4>
          <p>第二件半价</p>
        </li>
        <li>
          <img src="//gw.alicdn.com/bao/uploaded/i1/bao/upload/TB1FsZmrruWBuNjSszgwu28jVXa.png_360x360q75.jpg_.webp" alt="">
          <h4>呵护双眼 方便携带</h4>
          <p>爆款直降</p>
        </li>
      </ul>
    </div>
  </section>
  <div class="recommend-ad">
      <img src="../../../assets/images/home/home_img_banner06@2x.png" alt="">
    </div>
</div>

</template>

<script type="text/ecmascript-6">
export default {
  name: 'HomeRecommend',
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
.recommend-content {
  @include flex(row);
  height: 304px;
  .item {
    width: 50%;
    box-sizing: border-box;
    h4 {
      @include textEllipsis();
      font-size: 24px;
      color: $font000;
    }
    p {
      color: $Promotion;
      @include textEllipsis();
      font-size: 22px;
      margin: 8px 0 20px;
    }
    &:first-child {
      border-right: 1px solid #ddd;
      padding: 30px 24px 16px;
      img {
        width: 100%;
        height: 176px;
      }
    }
    ul {
      width: 100%;
      li {
        height: 152px;
        box-sizing: border-box;
        padding: 30px 24px 16px;
        img {
          float: right;
          width: 100px;
          height: 100px;
        }
        &:first-child {
          border-bottom: 1px solid #ddd;
        }
      }
    }
  }
}
.recommend-ad {
  height: 296px;
  img {
    width: 100%;
  }
}
</style>
