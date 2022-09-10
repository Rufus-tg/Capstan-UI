<demo>
触发方式为 hover
</demo>
<template>
<popover>
 <popover triggle="hover">
  <Button>上方弹出</Button>
   
  </popover>
</popover>
<popover position="bottom" triggle="hover">
  <Button>下方弹出</Button>
   
</popover>
<popover position="left" triggle="hover">
  <Button>左边弹出</Button>
   
</popover>
<popover position="right" triggle="hover">
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