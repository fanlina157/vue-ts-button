<template>
 <div class="1">
    fullName:{{fullName}}
  </div>
</template>
<script>
export default {
  props:{
    firstName: String,
  },
  data(){
    return {
      fullName:''
    }
  },
  watch: {
    // firstName(newName) {
    //   this.fullName = newName;
    // }
    firstName: {
      handler(newName, oldName) {
        this.fullName = newName
      },
      // 代表在wacth里声明了firstName这个方法之后立即先去执行handler方法
      immediate: true
    }
  }
}
</script>
<style lang="less" scoped>
</style>
