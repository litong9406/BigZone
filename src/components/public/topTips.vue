<template>
  <div class="top-tips">
    <span>{{title.title}}</span>
    <span v-if="title.unfold" class="unfold" @click="unflod">
      <span v-if="active"><i class="el-icon-arrow-up"></i>收起</span>
      <span v-else><i class="el-icon-arrow-down"></i>展开</span>
    </span>
  </div>
</template>
<script>
export default {
  data () {
    return {
      active: false
    }
  },
  methods: {
    unflod () {
      this.active = !this.active
      this.$emit('showList', this.active)
    }
  },
  props: ['title']
}
</script>
<style lang="scss" scoped>
@import '../../assets/style/mixins/var';
.top-tips{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: $gray-color;
  height:46px;
  padding:0 16px;
  .unfold{
    border:0;
    background-color: $gray-color;
    font-size: $xs-size;
    cursor: pointer;
    color:$text-gray-color;
    &:hover{
      color:$main-color;
    }
    i{
      margin-right: 4px;
    }
  }
}
</style>
