<template>
  <div class="search">
    <div class="search-in">
      <i class="icon-search"></i>
      <input type="text" placeholder="输入关键词搜索">
      <el-button type="primary" class="search-btn">搜索</el-button>
    </div>
    <el-button class="advanced-search">高级搜索</el-button>
  </div>
</template>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
.search{
    display: flex;
  .search-in{
    position: relative;
    width:430px;
    .icon-search{
      @include icon(12px,12px,'../../assets/image/icon/icon-search.png');
      position: absolute;
      top: 50%;
      left:10px;
      transform: translateY(-50%)
    }
    input[type='text']{
      border:1px solid $input-border-color;
      height:32px;
      border-radius: 4px;
      padding: 0 50px 0 30px;
      font-size: $xs-size;
      width:100%;
      &:focus{
        border-color:$main-color;
      }
    }
    .search-btn{
      padding: 9px 15px;
      position: absolute;
      right: 0;
      top: 0px;
      border-top-left-radius: 0;
      border-bottom-left-radius: 0;
    }
  }
  .advanced-search{
    padding: 8px 20px;
    margin-left: 5px;
  }
}
</style>
