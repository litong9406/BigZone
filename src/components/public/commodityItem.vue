<template>
  <div class="com-item">
    <div class="left">
      <el-checkbox class="comm-check"></el-checkbox>
      <div class="com-img">
        <img src="../../assets/image/user-head.jpg" alt="">
      </div>
    </div>
    <div class="right">
      <div class="topic">
        <div class="ercode">
          <i class="iconfont icon-erweima"></i>
          <div class="ercode-detail">
            <div class="top">
              <img src="../../assets/image/1523612362.png" alt="">
              <p class="comm-name">商品名称</p>
              <p class="comm-code">AX23578009812121</p>
            </div>
            <div class="download">
              <i class="iconfont icon-icon-"></i>下载
            </div>
          </div>
          <i class="ercode-tr"></i>
        </div>
        <div class="name">
          第三代谷歌智能沙发高配真皮多把手可分期
        </div>
      </div>
      <div class="com-info">
        <p>
          商品编号：AX52047528628638466
        </p>
        <p>
          货号：XX45207
        </p>
        <p class="type-list">
          <span>品类：沙发> 智能沙发</span>
          <span>品牌：谷歌</span>
          <span>规格：大型</span>
          <span>型号：ZA2000</span>
        </p>
      </div>
      <div class="change-price">
        <div class="price-view">
          <span class="black">建议零售价：</span>
          <span class="num" v-show="!isChangePrice">￥3000.00</span>
          <i class="el-icon-edit" v-show="!isChangePrice" @click="changePrice"></i>
        </div>
        <div class="price-op" v-show="isChangePrice">
          <input type="text">
          <el-button class="btn define">确定</el-button>
          <el-button class="btn cancel" @click="cancelChangePrice">取消</el-button>
        </div>
      </div>
      <div class="comm-label">
        <span class="label">滞销
          <i class="el-icon-delete"></i>
        </span>
        <span class="label">新品
          <i class="el-icon-delete"></i>
        </span>
        <span class="label">主推货
          <i class="el-icon-delete"></i>
        </span>
        <div class="add-label">
          <span class="add-btn" @click="addLable" v-show ="!isAddLabel">+ 添加</span>
          <span class="add-input" v-show ="isAddLabel">
            <input type="text">
            <el-button class="btn define">确定</el-button>
            <el-button class="btn cancel" @click="cancelAddLabel">取消</el-button>
          </span>
        </div>
      </div>
    </div>
    <div class="comm-opera">
      <el-button icon="el-icon-edit" @click="commEdit" circle></el-button>
      <el-button round>下架</el-button>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      isChangePrice: false,
      isAddLabel: false
    }
  },
  methods: {
    changePrice () {
      this.isChangePrice = true
    },
    cancelChangePrice () {
      this.isChangePrice = false
    },
    addLable () {
      this.isAddLabel = true
    },
    cancelAddLabel () {
      this.isAddLabel = false
    },
    commEdit () {
      this.$router.push({path: '/commodity/commEdit'})
    }
  }
}
</script>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
@import '../../assets/style/components/icon';
.com-item{
  &:hover{
    background: $gray-color;
    .comm-opera{
      display: block;
    }
  }
  border-bottom:1px solid $border-color;
  display: flex;
  padding: 18px 14px;
  position: relative;
  .comm-opera{
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    right:18px;
    display: none;
    button:nth-child(1){
      padding:7px;
      background-color:$main-color;
      border-color:$main-color;
      &:hover{
        background-color:lighten($main-color,6%);
        border-color:lighten($main-color,6%);
      }
      i{
        color:#fff;
      }
    }
    button:nth-child(2){
      padding:8px 12px;
      background-color:#DDE0E9;
      border-color:#DDE0E9;
      color:$text-main-color;
      &:hover{
        background-color:darken(#DDE0E9,6%);
        border-color:darken(#DDE0E9,6%);
      }
    }
    // display: none;
  }
  .left{
    display: flex;
    .comm-check{
      margin-top:34px;
    }
    .com-img{
      margin-left:12px;
      img{
        width:80px;
        height:80px;
      }
    }
  }
  .right{
    margin-left: 15px;
    .btn{
      padding:3px 8px;
      &.define{
        border-color: $main-color;
        color:$main-color;
      }
      &.cancel{
        border-color: $input-border-color;
        color:$text-main-color;
        margin-left: 4px;
      }
    }
    .topic{
      display: flex;
      .ercode{
        position: relative;
        width: 30px;
        &:hover{
          .ercode-detail{
            display: block;

          }
          .ercode-tr{
            display: inline;
          }
        }
       .icon-erweima{
         font-size: 22px;

       }
       .ercode-detail{
         display: none;
          width:204px;
          position: absolute;
          background: #fff;
          border:1px solid rgba(0,0,0,0.16);
          box-shadow: 0 6px 12px 0 rgba(0,0,0,0.2);
          z-index: 9;
          top: -120px;
          left: 30px;
          text-align: center;
          font-size: $xs-size;
          border-radius: 4px;
          .top{
            padding:14px 14px 0 14px;
          }
          .comm-code{
            color: $text-gray-color;
            margin-top: 4px;
          }
          img{
            width:175px;
            height:175px;
          }
          .download{
            border-top:1px solid $border-color;
            margin-top: 6px;
            padding: 8px 0;
            font-size: $xs-size;
            .iconfont{
              margin-right: 8px;
              font-size: 14px;
            }
          }
        }
          .ercode-tr{
            content: '';
            display: none;
            position: absolute;
            width:18px;
            height:18px;
            border:1px solid rgba(0, 0, 0, 0.16);
            background: #fff;
            transform: rotate(45deg);
            z-index: 10;
            border-right: 0;
            border-top: 0;
            border-radius: 4px;
          }
      }
      .name{
        font-size: $xlg-size;
      }
    }
    .com-info{
      font-size: $xs-size;
      color:$text-gray-color;
      margin: 9px 0;
      p{
        margin: 4px 0;
      }
      p.type-list{
        span{
          margin-right: 12px;
        }
      }
    }
    .change-price{
      font-size:$xs-size;
      display:flex;
      .price-view{
        .num{
          color:$text-red-color;
          font-weight: bold;
        }
        .el-icon-edit{
          margin-left: 4px;
          cursor: pointer;
          &:hover{
            color:$main-color;
          }
        }
      }
      .price-op{
        display: flex;
        margin-left: 4px;
        input[type='text']{
          border:1px solid $input-border-color;
          height:20px;
          border-radius: 4px;
          font-size: $xs-size;
          width:80px;
          padding-left:4px;
          margin-right: 4px;
        }
      }
    }
    .comm-label{
      font-size: $xs-size;
      margin-top: 14px;
      display: flex;
      .label{
        display: inline-block;
        border-radius: 4px;
        padding: 1px 6px;
        margin-right: 4px;
        &:hover{
          .el-icon-delete{
            display: inline-block;
          }
        }
        .el-icon-delete{
          display: none;
        }
        &:nth-child(n+1){
          color:#EB5C00;
          border:1px solid #EB5C00;
        }
        &:nth-child(n+2){
          color:#44AF7B;
          border:1px solid #44AF7B;
        }
        &:nth-child(n+3){
          color:#7180F1;
          border:1px solid #7180F1;
        }
      }
      .add-label{
        .add-btn{
          cursor: pointer;
          display: inline-block;
          border-radius: 4px;
          padding: 1px 6px;
          border:1px solid $input-border-color;
          color:$text-gray-color;
        }
        .add-input{
          input[type='text']{
            border:1px solid $input-border-color;
            height:20px;
            border-radius: 4px;
            font-size: $xs-size;
            width:80px;
            padding-left:4px;
            margin-right: 4px;
            padding-right: 14px;
          }
        }
      }
    }
  }
}
</style>
