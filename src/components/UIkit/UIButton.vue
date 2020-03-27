<template>
 <div>
   <!-- v-on="$listeners" 表示当前类的内部 不对button 事件监听  -->
    <!-- <button class="ui-button" v-on="$listeners">
      Button
    </button> -->

    <button class="ui-button" @click="childClick"
      :class="{
        'ui-button-small': small,
        'ui-button-large': large,
        'ui-button-squre': squre,
        'ui-button-rounded': rounded,
        'ui-button-circle': circle,
        'ui-button-disabled': disabled
      }"
      :style="{
        background: color
      }"
    >
      <slot>Button</slot>
    </button>
 </div>
</template>
<script lang="ts">
import {Component,Vue,Emit, Prop} from 'vue-property-decorator';
@Component
export default class UIButton extends Vue {

  // 父传子
  @Prop(Boolean) private large: boolean | undefined;
  @Prop(Boolean) private small: boolean | undefined;
  @Prop(Boolean) private squre: boolean | undefined;
  @Prop(Boolean) private rounded: boolean | undefined;
  @Prop(Boolean) private circle: boolean | undefined;
  @Prop(Boolean) private disabled: boolean | undefined;
  @Prop(String) private color: string | undefined;


  // computed
  // private get TintColor () {
  //   if(this.color) {
  //     return this.color
  //   }else {
  //     return '#2D8CF0'
  //   }
  // }

  // emit 装饰的是一个函数
  // 参数 要发送事件的名称
  @Emit('parentClick') 
  private emitClickEvent (event: MouseEvent) {
    console.log(11)
  }

  private mounted() {
    // console.log(this.small); 
    // console.log(this.large); 
    console.log(this.color); 
  }

  private childClick(event: MouseEvent) {

    if(!this.disabled){
      this.emitClickEvent(event)

    }
      //  this.$emit('parentClick',this.message)
      // 子组件点击 执行childClick 触发父组件方法parentClick
      //  <UIButton @parentClick="onClick"></UIButton>
      //  onClick: function (childValue) {
      //    childValue就是子组件传过来的值
      //  }
  }
}
</script>
<style lang="stylus" scoped>
//混合
// resize (minWidth, height, paddingLR, fontSize)
//   min-width minWidth
//   height height
//   padding 0 paddingLR
//   font-size  fontSize
//   &.ui-button-rounded, &.ui-button-circle
//       border-radius (@height / 2)
//   &.ui-button-circle
//       width @height  // width = height
//       min-width 0
//       padding 0
.ui-button
  // resize (64px, 36px, 16px, 15px)
  min-width 64px
  height 36px
  padding 0 16px
  font-size 15px
  border none 
  border-radius 4px
  color #17233D
  // background var(--color-tint)
  background #2D8CF0
  font-weight 500
  letter-spacing 2px
  cursor pointer
  user-select none
  outline none  
  &:hover 
    filter brightness(120%)
  &:active
    filter brightness(80%)
  &.ui-button-small 
      // resize (54px, 26px, 13px, 12px)
      min-width 54px
      height 26px
      padding 0 13px
      font-size 12px
    
  &.ui-button-large 
      // resize (78px, 44px, 19px, 18px)
      min-width 78px
      height 44px
      padding 0 19px
      font-size 18px
  &.ui-button-squre
      border-radius 0
  &.ui-button-rounded
      border-radius (@height / 2)
  &.ui-button-circle
      width @height
      border-radius (@height / 2)
      min-width 0
      padding 0
  &.ui-button-disabled
      color #c5c8ce
      background #f5f5f5
      cursor not-allowed
  
</style>  


