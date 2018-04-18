<template>
  <div class="comm-edit">
    <div class="top">
      <bread-crumb :breadcrumbList="breadcrumbList"></bread-crumb>
      <div class="change-sort">
        <span>品类：</span>
        <div class="sort">
          <ul>
            <li>家具</li>
            <li>客厅</li>
            <li>沙发</li>
          </ul>
        </div>
        <el-button size="mini" class="change">修改</el-button>
      </div>
    </div>
    <div class="form-group">
      <div class="form-block">
        <top-tips :title="necessary"></top-tips>
        <div class="form-list">
          <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="120px" class="ruleForm">
            <el-row :gutter="24">
              <el-col :span="12">
                <el-form-item label="活动名称" prop="name">
                  <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="定价方式" prop="resource">
                  <el-radio-group v-model="ruleForm.resource">
                    <el-radio label="议价"></el-radio>
                    <el-radio label="定价"></el-radio>
                  </el-radio-group>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="品牌系列" prop="region">
                  <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
                    <el-option label="区域一" value="shanghai"></el-option>
                    <el-option label="区域二" value="beijing"></el-option>
                  </el-select>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="建议零售价" prop="name">
                  <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="单位" prop="name">
                  <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="上架状态" prop="name">
                  <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="12">
                <el-form-item label="上架状态" prop="name">
                  <el-checkbox-group v-model="ruleForm.type">
                    <el-checkbox label="门店销售" name="type"></el-checkbox>
                    <el-checkbox label="微店销售" name="type"></el-checkbox>
                    <el-checkbox label="积分商城兑换" name="type"></el-checkbox>
                  </el-checkbox-group>
                </el-form-item>
              </el-col>
            </el-row>
          </el-form>
        </div>
      </div>
      <div class="form-block">
        <top-tips :title="optional" @showList="showList"></top-tips>
         <el-collapse-transition>
          <div class="form-list" v-show="thisShow">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="120px" class="ruleForm">
              <el-row :gutter="24">
                <el-col :span="12" :offset="12">
                  <el-form-item label="活动名称" prop="name" class="upload-item">
                    <el-upload
                      action="https://jsonplaceholder.typicode.com/posts/"
                      list-type="picture-card"
                      :on-preview="handlePictureCardPreview"
                      :on-remove="handleRemove">
                      <i class="el-icon-plus"></i>
                    </el-upload>
                    <el-dialog :visible.sync="dialogVisible">
                      <img width="100%" :src="dialogImageUrl" alt="">
                    </el-dialog>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="定价方式" prop="resource">
                    <el-radio-group v-model="ruleForm.resource">
                      <el-radio label="议价"></el-radio>
                      <el-radio label="定价"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="品牌系列" prop="region">
                    <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
                      <el-option label="区域一" value="shanghai"></el-option>
                      <el-option label="区域二" value="beijing"></el-option>
                    </el-select>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="建议零售价" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="单位" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
                <el-col :span="24">
                  <el-form-item label="属性规格" prop="name">
                    <el-input type="textarea" v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
                <el-col :span="24">
                  <el-form-item label="微店详情" prop="name">
                    <el-input type="textarea" v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="积分兑换方式" prop="resource">
                    <el-radio-group v-model="ruleForm.resource">
                      <el-radio label="议价"></el-radio>
                      <el-radio label="定价"></el-radio>
                    </el-radio-group>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="属性规格" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
                <el-col :span="12" :offset="12">
                  <el-form-item label="属性规格" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                  </el-form-item>
                </el-col>
              </el-row>
            </el-form>
          </div>
        </el-collapse-transition>
      </div>
      <div class="opeartion">
        <div>
          <el-button class="cancle">取消</el-button>
        </div>
        <div>
          <el-button class="submit_add">
            提交并继续创建
          </el-button>
          <el-button class="submit">
            提交
          </el-button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import breadCrumb from '../../../components/public/breadcrumb'
import topTips from '../../../components/public/topTips'
export default {
  data () {
    return {
      dialogVisible: false,
      dialogImageUrl: '',
      thisShow: false,
      breadcrumbList: [
        {title: '商品管理', path: '/commodity'},
        {title: '编辑商品', path: ''}
      ],
      necessary: {
        title: '必填信息',
        unfold: false
      },
      optional: {
        title: '选填信息',
        unfold: true
      },
      ruleForm: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      },
      rules: {
        name: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        region: [
          { required: true, message: '请选择活动区域', trigger: 'change' }
        ],
        date1: [
          { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
        ],
        date2: [
          { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
        ],
        type: [
          { type: 'array', required: true, message: '请至少选择一个活动性质', trigger: 'change' }
        ],
        resource: [
          { required: true, message: '请选择活动资源', trigger: 'change' }
        ],
        desc: [
          { required: true, message: '请填写活动形式', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleRemove (file, fileList) {
      console.log(file, fileList)
    },
    handlePictureCardPreview (file) {
      this.dialogImageUrl = file.url
      this.dialogVisible = true
    },
    showList (data) {
      if (data) {
        this.thisShow = data
      } else {
        this.thisShow = false
      }
    }
  },
  components: {breadCrumb, topTips}
}
</script>
<style lang="scss" scoped>
@import '../../../assets/style/mixins/var';
.comm-edit{
  width:1000px;
  margin:0 auto;
  .top{
    .change-sort{
      text-align: center;
      margin-top: 16px;
      .sort{
        display: inline-block;
        margin:0 8px;
        li{
          display: inline-block;
          &:nth-child(n+2)::before{
            content: '>',
          }
        }
      }
      .change{
        padding:5px 12px;
        color:$text-gray-color;
        &:hover{
          color:$main-color;
        }
      }
    }
  }
  .form-group{
    margin-top: 20px;
    .form-block{
      .form-list{
        margin-top: 28px;
        padding: 0 70px;
        .upload-item{
          .el-form-item__content{
            line-height: 0;
          }
        }
      }
    }
    .opeartion{
      display: flex;
      justify-content: space-between;
      margin: 50px 0;
      button{
        padding:13px 40px;
      }
      .submit{
          @include linear-grad;
          color:#fff;
          padding:14px 40px;
          border:0;
          &:hover{
            opacity: 0.9;
          }
      }
    }
  }
}
</style>
