<template>
  <div id="app">
    <Home />
    <!-- <hh /> -->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Home from '@/Home.vue'
// import hh from '@/1.vue'
@Component({
  components:{
    Home,
    // hh
  }
})
export default class App extends Vue {
  
}
</script>

<style lang="stylus">
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>
