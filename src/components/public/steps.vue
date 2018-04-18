<template>
  <div class="steps">
    <el-steps :active="active" finish-status="success" align-center>
      <el-step title="下载模板"></el-step>
      <el-step title="上传文件"></el-step>
      <el-step title="完成"></el-step>
    </el-steps>
    <div class="step-list">
      <div class="step-item" v-show="active===1">
        <div class="item-bg">
          <a href="http://"><img src="../../assets/image/icon/icon-filedown.png" alt="" class="icon-filedown"></a>
        </div>
        <p>商品信息模版下载</p>
      </div>
      <div class="step-item" v-show="active===0">
        <p></p>
        <el-upload
          class="upload-block"
          drag
          action="https://jsonplaceholder.typicode.com/posts/"
          multiple>
          <i class="el-icon-upload"></i>
          <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
          <div class="el-upload__tip" slot="tip">
            <p>支持扩展名：.xls .csv .xslx</p>
          </div>
        </el-upload>
      </div>
    </div>
    <div class="foot-tips">
      <div class="tips">
        <p v-show="active===0">若已有模板，可直接点击【下一步】，跳过此步骤</p>
      </div>
      <el-button @click="next">下一步</el-button>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      active: 0
    }
  },
  methods: {
    next () {
      if (this.active++ > 2) this.active = 0
    }
  }
}
</script>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
.steps{
  margin-top: 30px;
  .foot-tips{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 40px;
    .tips{
      p{
        font-size: $xs-size;
      }
    }
  }
  .step-list{
    height: 300px;
    padding:40px 100px;
    display: flex;
    align-items: center;
    .step-item{
      height: 100%;
      flex: 1;
      text-align: center;
      .icon-filedown{
        width:60px;
      }
      .item-bg{
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 auto;
        a{
          width: 100px;
          height: 100px;
          background-image: linear-gradient(180deg,rgba(218, 234, 245, 0.8),rgba(183, 211, 232, 1));
          border-radius: 4px;
          img{
            margin-top: 26px;
          }
        }
      }
      p{
        font-size: $xs-size;
        color:$text-gray-color;
        text-align: center;
        margin-top: 10px;
      }
      .upload-block{
        border:1px dashed $main-color;
      }
    }
  }
}
</style>
