<demo>
每次只展开一个面板
</demo>
<template>
<collapse :selected="selected" single>
  <collapseItem title="标题1" name="1">内容1</collapseItem>
  <collapseItem title="标题2" name="2">内容2</collapseItem>
  <collapseItem title="标题3" name="3">内容3</collapseItem>
</collapse>
</template>

<script lang="ts">
import {
  collapse,
  collapseItem

} from "../lib/index";
export default {
  data() {
  return {
    selected: "1",
  };
},
  components: {
   collapse,
  collapseItem
  },
  setup() {
    
  }
}
</script>
<style lang="scss" scoped>

</style>