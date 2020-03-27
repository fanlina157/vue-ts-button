<template>
 <div class="1">
    <p>FirstName: <input type="text" v-model="firstName"></p>
    <child :firstName="firstName"></child>
  </div>
</template>
<script>
import child from '@/2.vue'
export default {
  components:{
    child
  },
  data(){
    return {
      firstName: 'Dawei',
      fullName:''
    }
  }
}
</script>
<style lang="less" scoped>
</style>
