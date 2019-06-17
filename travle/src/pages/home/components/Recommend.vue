<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <img class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  }
//   data () {
//     return {
//       recommendList: [{
//         id: '001',
//         imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_200x200_1bc99086.jpg',
//         title: '故宫',
//         desc: '故宫故宫故宫故宫'
//       }, {
//         id: '002',
//         imgUrl: 'http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_200x200_99ae30ee.jpg',
//         title: '北京欢乐谷',
//         desc: '北京欢乐谷北京欢乐谷'
//       }, {
//         id: '003',
//         imgUrl: 'http://img1.qunarzz.com/sight/p0/1708/2b/2b3b94de99c0a425a3.img.jpg_200x200_2458ffb2.jpg',
//         title: '八达岭长城',
//         desc: '八达岭长城八达岭长城'
//       }]
//     }
//   }
}
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
 .title
   margin-top : .2rem
   line-height : .8rem
   background : #eeeeee
   text-indent : .2rem
 .item
   overflow : hidden
   display : flex
   height : 1.9rem
   .item-img
     width : 1.7rem
     height : 1.7rem
     padding : .1rem
    .item-info
      flex : 1
      padding : .1rem
      min-width : 0
      .item-title
        line-height : .54rem
        font-size : .32rem
        ellipsis()
      .item-desc
        line-height : .4rem
        color : #ccc
        ellipsis()
      .item-button
        line-height : .44rem
        margin-top : .16rem
        background : #ff9300
        padding : 0 .2rem
        border-radius : .06rem
        color : #fff
</style>
