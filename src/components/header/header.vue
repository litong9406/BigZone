<template>
  <div class="header">
    <div class="logo">
      <!-- <img src="../../assets/image/logo_bigzone.svg" alt=""> -->
      <i class="iconfont icon-logo_bigzone1"></i>
    </div>
    <div class="nav">
      <ul>
        <li :class="{active: $route.path === '/'}">
          <router-link to="/" >首页</router-link>
        </li>
        <li v-for="(item, index) in navList" :key="index" :class="{active: $route.path.indexOf(item.path) !== -1 && $route.path !== '/'}">
        <router-link :to="item.path">{{item.title}}</router-link>
        </li>
        <li>
          <router-link to="/" >营销</router-link>
        </li>
        <li>
          <router-link to="/" >营销</router-link>
        </li>
        <li>
          <router-link to="/" >营销</router-link>
        </li>
        <li>
          <router-link to="/" >营销</router-link>
        </li>
        <li>
          <router-link to="/" >营销</router-link>
        </li>
      </ul>
    </div>
    <div class="user">
      <p class="icon-lb">
        <i class="iconfont icon-cion_tips"></i>
      </p>
      <p class="icon-lb">
        <i class="iconfont icon-icon_message"></i>
      </p>
      <p class="user-head">
          <img src="../../assets/image/user-head.jpg" alt="">
      </p>
      <div class="user-info">
        <p class="text-ellipsis">王志国</p>
        <p class="text-ellipsis">某门店经销商</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      navList: [
        {
          title: '商品',
          path: '/commodity'
        },
        {
          title: '订单',
          path: '/order'
        }
      ]
    }
  },
  computed: {
  }
}
</script>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
.header{
  display:flex;
  flex:1;
  height:60px;
  justify-content: space-between;
  @include linear-grad;
  .logo{
    flex: 0 0 150px;
    margin: 4px 0 0 25px;
    .iconfont{
      color:#fff;
      font-size: 48px;
    }
  }
  .nav{
    flex: 1;
    margin: 0 50px;
    max-width: 1000px;
    ul{
      display: flex;
      height: 100%;
      li{
        flex: 1;
        line-height: 60px;
        text-align: center;
        position: relative;
        &:hover{
          background: rgba(0,0,0,0.1);
        }
        &.active{
          background: rgba(0,0,0,0.1);
          &::after{
            @include active-triangle(5px, $text-header-color);
          }
        }
        a{
          color: $text-header-color;
          font-size: $md-size;
          display: inline-block;
          width: 100%;
        }
      }
    }
  }
  .user{
    flex: 0 0 250px;
    .icon-lb{
      display: inline-block;
      margin-top:16px;
      margin-right:10px;
      .iconfont{
        color:#fff;
        font-size: 29px;
      }
      // .icon-help{
      //   @include icon(28px,28px,"../../assets/image/icon/icon-help.png");
      // }
      // .icon-remind{
      //   @include icon(28px,28px,"../../assets/image/icon/icon-remind.png");
      // }
    }
    .user-head{
      display: inline-block;
      position: relative;
      top:3px;
      img{
        width:26px;
        height:26px;
        border-radius: 50%;
        &:hover{
          box-shadow: 0 0 0 2px #fff;
        }
      }
    }
    .user-info{
      display: inline-block;
      max-width: 100px;
      position: relative;
      top: 5px;
      margin-left: 5px;
      p{
        color:$text-header-color;
        font-size: $md-size;
        &:nth-child(2){
          font-size: $xs-size;
        }
      }
    }
  }
}
</style>
