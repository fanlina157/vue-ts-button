<template>
  <div>
    <div class="btn-container">
      <UIButton @parentClick="onClick" 
      color="yellow"
      :small="small" 
      :large="large"
      :squre="squre"
      :rounded="rounded"
      :circle="circle"            
      :disabled="disabled"            
      ></UIButton>
    </div>
    <div class="btn-group">
      <button class="btn" @click='resize("small")'>小</button>
      <button class="btn" @click='resize("normal")'>正常</button>
      <button class="btn" @click='resize("large")'>大</button>
    </div>
    <div class="btn-group">
      <button class="btn" @click='changeRadius("squre")'>方形</button>
      <button class="btn" @click='changeRadius("normal")'>正常</button>
      <button class="btn" @click='changeRadius("rounded")'>半圆</button>
      <button class="btn" @click='changeRadius("circle")'>圆形</button>
    </div>
    <div class="btn-group">
      <button class="btn" @click='changeDisabled'>禁用</button>
    </div>
  </div>
</template>
 
 
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import UIButton from '@/components/UIkit/UIButton.vue';
@Component({
  components: {
    UIButton
  }
})
export default class Home extends Vue {
  private large = false;
  private small = false;
  private squre = false;
  private rounded = false;
  private circle = false;
  private disabled = false;

  private onClick(event: MouseEvent) {
    console.log(event);
  }

  // 大小
  private resize(size: string) {
    switch (size) {
      case 'small':
        this.large = false;
        this.small = true;
        break;
      case 'normal':
        this.large = false;
        this.small = false;
        break;
      case 'large':
        this.large = true;
        this.small = false;
        break;
    }
  }

  // radius
  private changeRadius(radius: string) {
    switch (radius) {
      case 'squre':
        this.squre = true;
        this.rounded = false;
        this.circle = false;
        break;
       case 'normal':
        this.squre = false;
        this.rounded = false;
        this.circle = false;
        break;
      case 'rounded':
        this.squre = false;
        this.rounded = true;
        this.circle = false;
        break;
      case 'circle':
        this.squre = false;
        this.rounded = false;
        this.circle = true;
        break;
    }
  }

  // disabled
  private changeDisabled() {
    this.disabled = !this.disabled
  }
}
</script>
 
 
<style lang="stylus" scoped>
.btn-container {
  height: 100px;
}

.btn-group {
  display: flex;
}

.btn {
  margin: 0 5px;
}
</style>