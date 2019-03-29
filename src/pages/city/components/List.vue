<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div v-for="item of hot"
          :key="item.id"
          @click="handleCityClick(item.name)"
          class="button-wrapper">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area"
      v-for="(item, key) of cities"
      :key="key"
      :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <ul class="item-list">
          <li class="border-bottom"
          v-for="innerItem of item"
          :key="innerItem.id"
          @click="handleCityClick(innerItem.name)">{{innerItem.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import BScroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  data () {
    return {

    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true
    })
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
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
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
@import '~@/assets/styles/varibles.scss';

.border-topbottom {
  &:before {
    border-color: #ccc;
  }
  &:after {
    border-color: #ccc;
  }
}
.border-bottom {
  &:before {
    border-color: #ccc;
  }
}
.list {
  overflow: hidden;
  position: absolute;
  top: 160px;
  left: 0;
  right: 0;
  bottom: 0;
  background: #fff;
  .title {
    line-height: 50px;
    background: #eee;
    color: $font666;
    padding-left: 20px;
    font-size: 26px;
  }
}
.button-list {
  padding: 10px 60px 10px 10px;
  overflow: hidden;
  .button-wrapper {
    float: left;
    width: 33.33%;
    .button {
      margin: 10px;
      padding: 10px 0;
      border-radius: 3px;
      text-align: center;
      border: 2px solid #ccc;
    }
  }
}
.item-list {
  li {
    line-height: 76px;
    color: #666;
    padding-left: 20px;
    cursor: pointer;
  }
}
</style>
