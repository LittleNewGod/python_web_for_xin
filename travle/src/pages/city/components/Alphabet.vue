<template>
  <ul class="list">
    <li class="item" v-for="letter of letters" :key="letter" @click="handleLettleClick" @touchstart="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd" :ref="letter">{{letter}}</li>
    <!-- <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li> -->
  </ul>
</template>
<script>
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
  update () {
    this.startY = this.$refs['A'][0].offsetTop// 此处求出A距离本组件顶部的高度
  },
  methods: {
    handleLettleClick (e) {
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
          const touchY = e.touches[0].clientY - 79// 此处求出当前鼠标位置距离本组件顶部的高度，79是Header,Search组件的高度
          const index = (Math.floor((touchY - this.startY) / 22)) - 2// 此处求出当前处于第几个字母
          console.log(index)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 20)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>
<style lang="stylus" scoped>
 @import '~styles/varibles.styl'
 .list
   display : flex
   flex-direction : column
   justify-content : center
   position : absolute
   top : 1.58rem
   right : 0
   bottom : 0
   width : .4rem
   .item
    line-height : .44rem
    text-align : center
    color : $bgColor
</style>
