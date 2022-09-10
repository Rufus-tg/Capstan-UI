<demo>
简单展示
</demo>
<template>
<guluinput value="中文"></guluinput>
<guluinput value="禁用" disabled></guluinput>
<guluinput value="只读" readonly></guluinput>
<guluinput value="错误" :error="error"></guluinput>
</template>

<script lang="ts">
import {
  guluinput

} from "../lib/index";
export default {
data() {
  return {
    error: '输入内容错误'
  }
},
  components: {
  guluinput
  },
  setup() {
    
  }
}
</script>
<style lang="scss" scoped>

</style>