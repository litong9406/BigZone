<template>
  <div class="label-role">
    <el-table
    :data="tableData"
    style="width: 100%">
    <el-table-column
      prop="date"
      label="标签"
      align="center"
      width="200">
    </el-table-column>
    <el-table-column
      prop="name"
      label="规则"
      align="center"
      width="300">
    </el-table-column>
    <el-table-column
      prop="address"
      align="center"
      width="300"
      label="备注">
    </el-table-column>
    <el-table-column label="操作" align="center">
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)" class="edit">编辑</el-button>
        <el-button
          size="mini"
          @click="handleDelete(scope.$index, scope.row)" class="delete">启用</el-button>
      </template>
    </el-table-column>
  </el-table>
  </div>
</template>
<script>
export default {
  data () {
    return {
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }]
    }
  },
  methods: {
    handleEdit (index, row) {
      console.log(index)
    },
    handleDelete (index, row) {
    }
  }
}
</script>
<style lang="scss" scoped>
@import '../../../assets/style/mixins/var';
.label-role{
  width:1000px;
  margin:0 auto;
  .el-table{
    margin-top: 16px;
  }
  .edit, .delete{
    border: 0;
    background: none;
  }
  .edit{
    color:$main-color;
    &:hover{
      color:lighten($main-color, 12%)
    }
  }
  .delete{
    color:$table-text-color;
    &:hover{
      color:lighten($table-text-color, 12%)
    }
  }
}
</style>
