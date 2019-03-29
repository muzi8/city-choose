<template>
  <ul class="list">
    <li class="item"
    v-for="item of letters"
    :key="item"
    :ref="item"
    @touchstart.prevent="handleTouchStart"
    @touchmove="handleTouchMove"
    @touchend="handleTouchEnd"
    @click="handleLetterClick">
    {{item}}</li>
  </ul>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          // const startY = this.$refs['A'][0].offsetTop
          const touchY = e.touches[0].clientY - 160
          const index = Math.floor((touchY - this.startY) / 40)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/layout.scss';
@import '~@/assets/styles/varibles.scss';
.list {
  @include flex(column, flex);
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 158px;
  right: 0;
  bottom: 0;
  width: 40px;
  .item {
    line-height: 40px;
    width: 100%;
    text-align: center;
    color: $bgColor;
  }
}
</style>
