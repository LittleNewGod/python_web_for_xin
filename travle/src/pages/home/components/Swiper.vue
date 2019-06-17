<template>
  <div class="wrapper">
      <swiper :options="swiperOption" v-if="showSwiper">
        <!-- slides -->
        <swiper-slide v-for="item of list" :key="item.id">
            <img class="swiper-img" :src="item.imgUrl" />
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
        <!-- <div class="swiper-button-prev" slot="button-prev">向前箭头</div>
        <div class="swiper-button-next" slot="button-next">向后箭头</div>
        <div class="swiper-scrollbar"   slot="scrollbar">滚动条</div> -->
      </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  // data: function(){
  //     这是定义子组件数据ES5写法
  // }
  data () {
  // 这是定义子组件数据ES6写法
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true, // 循环轮播作用
        autoplay: 3000
      }
      // swiperList: [{
      //   id: '001',
      //   imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20196/e440c31af79c0b9d1a1e84c577205562.jpg_750x200_0729c45b.jpg'
      // }, {
      //   id: '002',
      //   imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20195/6ab65be3878a5ea365514cf3a8125fd1.jpg_750x200_7b2fe404.jpg'
      // }, {
      //   id: '003',
      //   imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20195/aef5f8864f5a1167599609307571b2c4.jpg_750x200_db7bedbe.jpg'
      // }]
    }
  },
  props: {
    list: Array
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
 .wrapper >>> .swiper-pagination-bullet-active
   background : #fff
   margin : 8px
 .wrapper
   background : #eee
   overflow : hidden
   width : 100%
   height : 0
   padding-bottom : 26.67%
   .swiper-img
     width: 100%
</style>
