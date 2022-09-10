<demo>
简单使用
</demo>
<template>
<popover>
  <Button>上方弹出</Button>
   
</popover>
<popover position="bottom">
  <Button>下方弹出</Button>
   
</popover>
<popover position="left">
  <Button>左边弹出</Button>
   
</popover>
<popover position="right">
  <Button>右边弹出</Button>
</popover>
</template>

<script lang="ts">
import {
  popover,
  Button

} from "../lib/index";
export default {
  components: {
  popover,
  Button
  },
  setup() {
    
  }
}
</script>
<style lang="scss" scoped>
button{
  margin: 10px;
}
</style>