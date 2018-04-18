<template>
  <div class="sort-manage">
    <div class="top">
      <div class="opera">
        <el-checkbox class="comm-check">全选</el-checkbox>
        <el-button icon="el-icon-delete" class="delete">删除</el-button>
      </div>
      <search></search>
    </div>
    <div class="coll-list">
      <el-tree :data="treeList"  show-checkbox node-key="id"  ref="tree" @node-click="nodeClick">
        <div class="custom-tree-node" slot-scope="{ node, data }">
          <tree-list :node="node" :data="data" @appendTree="appendTree" @deleteTree="deleteTree"></tree-list>
        </div>
      </el-tree>
    </div>
    <div class="pagin">
        <span class="total">共400条数据</span>
        <el-pagination
        :page-size="100"
        layout="prev, pager, next, jumper"
        :total="400">
      </el-pagination>
    </div>
  </div>
</template>
<script>
import search from '../../../components/public/search'
import treeList from '../../../components/public/treeList'
export default {
  data () {
    return {
      treeList: [
        {
          id: 1,
          label: '分类 1',
          children: [{
            id: 4,
            label: '二级 1-1',
            children: [{
              id: 9,
              label: '三级 1-1-1'
            }, {
              id: 10,
              label: '三级 1-1-2'
            }]
          }]
        },
        {
          id: 2,
          label: '一级 2',
          children: [{
            id: 5,
            label: '二级 2-1'
          }, {
            id: 6,
            label: '二级 2-2'
          }]
        },
        {
          id: 3,
          label: '一级 3',
          children: [{
            id: 7,
            label: '二级 3-1'
          }, {
            id: 8,
            label: '二级 3-2'
          }]
        },
        {
          id: 4,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        },
        {
          id: 5,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        },
        {
          id: 6,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        },
        {
          id: 7,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        },
        {
          id: 8,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        },
        {
          id: 9,
          label: '一级 3',
          children: [{
            id: 8,
            label: '二级 3-1'
          }, {
            id: 9,
            label: '二级 3-2'
          }]
        }
      ]
    }
  },
  methods: {
    appendTree (data) {
      console.log(data)
      const newChild = { id: '', label: '分类', children: [] }
      if (!data.children) {
        this.$set(data, 'children', [])
      }
      data.children.push(newChild)
    },
    deleteTree (params) {
      const parent = params.node.parent
      const children = parent.data.children || parent.data
      const index = children.findIndex(d => d.id === params.data.id)
      children.splice(index, 1)
    },
    nodeClick (node) {
      console.log(node)
    }
  },
  components: {search, treeList}
}
</script>
<style lang="scss" scoped>
@import '../../../assets/style/mixins/var';
.sort-manage{
  width:1000px;
  margin:0 auto;
  .top{
    display: flex;
    flex:1;
    justify-content: space-between;
    padding: 0 18px;
    .opera{
      display: flex;
      .comm-check{
        margin-top: 6px;
        margin-right: 20px;
      }
      .delete{
        border:0;
        color:$main-color;
        padding:0px;
      }
    }
  }
  .coll-list{
    margin-top: 36px;
    .custom-tree-node{
      flex:1;
    }
  }
}
</style>
