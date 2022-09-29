<template>
  <div id="mask" v-show="visible" ref="mask">
   <div class="dialogBody" ref="dislogBody">
    <div class="dialog-heard">
      <div class="dialog-title">{{title}}</div>
      <div v-show="closeVisible" @click="close" class="closeIcon">X</div>
    </div>
    <div class="dislog-content">
      <slot></slot>
    </div>
    <slot name="footer"></slot>
   </div>
  </div>
</template>

<script>
export default {
  name: 'baby-dialog',
  props: {
    visible:{
      type:Boolean,
      default:false
    },
    title:{
      type:String,
    default:'提示'
  },
  closeVisible:{
    type:Boolean,
    default:true
  },
  width:{
    type:String,
    default:'200px'
  },
  height:{
    type:String,
    default:'200px'
  },
  destroys:{
    type:Boolean,
    default:false
  }
  },
  data(){
    return{
      
    }
  },
  mounted(){
    this.$refs.dislogBody.style.width=this.width;
    this.$refs.dislogBody.style.height=this.height;
    this.$refs.dislogBody.style.setProperty('--width',this.width);
    this.$refs.dislogBody.style.setProperty('--height',this.height);
    // this.$refs.mask.style.height = document.documentElement.clientHeight + 'px';
    我试试
  },
  methods:{
    close(){
       this.$emit('update:visible',false)
    }
  },
  watch:{
    visible:{
      immediate: true,
      handel(newVal,oldVal){
      if(newVal===true){
        this.$emit('open')
      }else{
      $this.$destroy()
    }
    }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
#mask{
  width: 100%;
  height: 100vh;
  opacity: 0.6;
  background-color: black;
  bottom: 0;
  left: 0;
  position: fixed;
  z-index: 998;
}
.dialogBody{
  z-index: 999;
  height: 200px;
  width: 200px;
  position: fixed;
  background: #fff;
  left: calc((100% - var(--width))/2);
  top: calc((100vh - var(--height))/2);
}
.dialog-heard{
  height: 34px;
  padding: 10px;
  border-bottom: 1px solid rgb(232, 227, 227);
}
.dialog-title{
  font-size: 14px;
  color: #000;
  height: 34px;
  width: 90%;
  line-height: 34px;
  text-align: left;
  display: inline-block;
}
.closeIcon{
  color: #262626;
  float: right;
  cursor: pointer;
  height: 34px;
  line-height: 34px;
  display: inline-block;
}
.dislog-content{
  width: 100%;
  height: calc(100% - 100px);
}
</style>
