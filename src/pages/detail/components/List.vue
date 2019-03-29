<template>
  <div>
    <div class="item" v-for="(item, index) of list" :key="index">
      <div class="item-title">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'DetailList',
  props: {
    list: Array
  },
  data () {
    return {

    }
  },
  components: {

  }
}
</script>

<style lang="scss" scoped>
.item {
  .item-title {
    line-height: 80px;
    font-size: 32px;
    padding: 0 20px;
    border-bottom: 1px solid #d8d8d8;
    .item-title-icon {
      position: relative;
      left: 2px;
      top: 6px;
      display: inline-block;
      width: 36px;
      height: 36px;
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -45px no-repeat;
      margin-right: 10px;
      background-size: 40px 300px;
    }
  }
  .item-children {
    padding: 0 20px;
  }
}
</style>
