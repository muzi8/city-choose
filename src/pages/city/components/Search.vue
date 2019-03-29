<template>
<div>
  <div class="search">
    <input v-model="keyword" class="search-input" type="text" placeholder="请输入城市名或拼音" />>
  </div>
  <div class="search-content"
      ref="search"
      v-show="keyword">
    <ul>
      <li class="search-item border-bottom"
      v-for="item of list"
      :key="item.id"
      @click="handleCityClick(item.name)">
        {{item.name}}
      </li>
      <li v-show="hasNoData" class="search-item border-bottom">
        没有找到匹配数据
      </li>
    </ul>
  </div>
</div>

</template>

<script type="text/ecmascript-6">
import BScroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'citySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 ||
                value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  methods: {
    handleCityClick (city) {
      // this.$store.dispatch('changeCity', city)
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
@import '~@/assets/styles/varibles.scss';
.search {
  height: 72px;
  background: $bgColor;
  padding: 0 10px;
  .search-input {
    width: 100%;
    height: 62px;
    line-height: 62px;
    text-align: center;
    border-radius: 6px;
    font-size: 28px;
    color: $font666;
    padding: 0 20px;
    box-sizing: border-box;
  }
}
.search-content {
  position: absolute;
  top: 160px;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
  background: #eee;
  overflow: hidden;
  .search-item {
    line-height: 62px;
    padding-left: 20px;
    color: #666;
    background: #fff;
  }
}
</style>
