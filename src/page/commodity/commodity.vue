<template>
  <div class="main">
  <div class="commodity">
    <div class="fix-header">
      <x-header></x-header>
      <child-nav :navList="navList"></child-nav>
    </div>
    <router-view class="main-cont"></router-view>
  </div>
    <x-footer></x-footer>
  </div>
</template>
<script>
import xHeader from '../../components/header/header'
import childNav from '../../components/public/childNav'
import xFooter from '../../components/footer/footer'
export default {
  data () {
    return {
      navList: [{
        title: '商品管理',
        path: '/commodity'
      },
      {
        title: '商品分类管理',
        path: '/commodity/sortManage'
      },
      {
        title: '品牌/系列管理',
        path: '/commodity/brandsManage'
      },
      {
        title: '标签规则',
        path: '/commodity/labelRoles'
      }]
    }
  },
  components: {xHeader, childNav, xFooter}
}
</script>
<style lang="scss" scoped>
.commodity{
  min-height: 100%;
  height: auto !important;
  height: 100%;
  margin: 0 auto -40px;
  padding-bottom: 40px;
  .fix-header{
    position: fixed;
    left:0;
    right:0;
    top:0;
    z-index: 9;
    min-width: 1080px;
  }
  .main-cont{
    padding-top:126px;
  }
}
</style>
