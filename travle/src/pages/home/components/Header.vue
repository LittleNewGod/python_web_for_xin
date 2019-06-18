<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题</div>
        <router-link to="/city">
          <div class="header-right">
              {{this.city}}
              <span class="iconfont arrow-icon">&#xe64a;</span>
          </div>
        </router-link>
    </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style lang="stylus" scoped>
//@import '../../../assets/styles/varibles.styl'
// @import '~@/assets/styles/varibles.styl' //此处修改地址为下面的方式，是因为改了webpack.base.conf.js文件的配置
 @import '~styles/varibles.styl'
 .header
    display : flex
    line-height : $headerHeight
    background : $bgColor
    color : #fff
    .header-left
      width : .64rem
      float : left
      .back-icon
        text-align : center
        font-size : 0.4rem
    .header-input
      flex : 1
      background : #fff
      height : .64rem
      line-height : .64rem
      margin-top : .12rem
      margin-left : .2rem
      border-radius : .1rem
      color : #ccc
      padding-left : 0.2rem
    .header-right
      width : 1.24rem
      float : right
      text-align : center
      color : #fff
      .arrow-icon
        font-size : .24rem
        margin-left : -.04rem
</style>
