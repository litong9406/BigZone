<template>
<div class="tree-item">
    <div class="left-label">
      <span v-show="!isEdit">{{ node.label }}</span>
      <div class="edit" v-show="isEdit">
        <input type="text" @click.stop="() =>{}" v-model="labelName">
        <el-button class="btn define" @click.stop="define(node,data)">确定</el-button>
        <el-button class="btn cancel" @click.stop="cancel">取消</el-button>
      </div>
    </div>
    <div class="operate-btns">
      <el-button icon="el-icon-edit" @click.stop="edit(node,data)" circle></el-button>
      <el-button circle class="node" icon="iconfont icon-icon_addsbject" @click="append(data)">
        <!-- <i class="icon-node"></i> -->
      </el-button>
      <el-button icon="el-icon-delete" @click.stop="remove(node,data)" circle></el-button>
    </div>
    </div>
  <!-- <div class="custom-tree-node" slot-scope="{ node, data }">
  </div> -->
</template>
<script>
export default {
  data () {
    return {
      isEdit: false,
      labelName: ''
    }
  },
  methods: {
    edit (node, data) {
      this.isEdit = true
      console.log(node)
    },
    append (data) {
      this.$emit('appendTree', data)
    },
    remove (node, data) {
      console.log(node)
      this.$emit('deleteTree', {node, data})
    },
    cancel () {
      this.isEdit = false
    },
    define (node, data) {
      this.isEdit = false
      console.log(data)
      data.label = this.labelName
    }
  },
  props: ['node', 'data']
}
</script>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
.tree-item{
  display: flex;
  justify-content: space-between;
  flex: 1;
  align-items: center;
  .left-label{
    display: flex;
    margin-left: 24px;
    .edit{
      input[type='text']{
        border:1px solid $input-border-color;
        height:28px;
        border-radius: 4px;
        font-size: $xs-size;
        width:180px;
        padding-left:4px;
        margin-right: 4px;
      }
      .btn{
        padding:7px 12px;
        &.define{
          border-color: $main-color;
          color:#FFF;
          background-color: $main-color;
        }
        &.cancel{
          border-color: $input-border-color;
          color:$text-main-color;
          margin-left: 4px;
        }
      }
    }
  }
  .operate-btns{
    display: none;
    button{
      padding:7px;
      background-color:$main-color;
      border-color:$main-color;
      height: 28px;
      &.node{
        padding: 5px;
        position: relative;
        top:1px;
      }
      &:hover{
        background-color:lighten($main-color,6%);
        border-color:lighten($main-color,6%);
      }
      i{
        color:#fff;
      }
    }
    .node{
      .iconfont{
        font-size: 24px;
        font-style: normal;
        font-weight: 400;
      }
    }
  }
}

// .el-tree-node__content:hover{
//   .operate-btns{
//     display: block;
//   }
// }
.right{
  margin-right: 20px;
  display: none;
  button{
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
  .node{
    padding:0;
    width:28px;
    height:29px;
    position: relative;
    top:6px;
    span{
      display: inline-block;
      width:100%;
      height:100%;
    }
  }
  .icon-node{
    @include icon(24px,24px,'../../assets/image/icon/icon-node.png')
  }
}
.parent-coll{
    border-top: 0;
    border-bottom:1px solid $border-color;

  .el-collapse{
    border-top: 0;
    border-bottom:0;
  }
  .el-coll{
    .item{
      padding:0 18px;
      justify-content: space-between;
      display: flex;
      &:hover{
        background-color:#E9EBF2;
        .right{
          display: block;
        }
      }
      .check{
        display: inline;
      }
      .label{
        margin-left: 32px;
        font-size:$md-size;
      }
    }
    .child-list{
      .el-coll{
        .item{
          padding-left: 40px;
        }
      }
    }
  }
}

</style>
