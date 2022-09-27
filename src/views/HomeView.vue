<template>
  <div class="home">
    <el-button type="button" @click="dialogVisible = true">点击打开 Dialog</el-button>
    <Bdialog
    :visible.sync="dialogVisible"
    :closeVisible="true"
    title="哈哈哈哈哈try again"
    width="750px"
    height="400px"
    >
  <span>你试试内容</span>
  <div class="redContent"></div>
  <template slot="footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </template>
</Bdialog>
  </div>
</template>

<script>
// @ is an alias to /src
import Bdialog from '@/components/Bdialog.vue';

export default {
  name: 'HomeView',
  components: {
    Bdialog,
},
data() {
      return {
        dialogVisible: false
      };
    }
}
</script>
<style lang="less" scoped>
   .redContent{
    width: 50px;
    height: 50px;
    background: #273;
   }
</style>