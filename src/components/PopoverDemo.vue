<template>
 <h1>popover 示例</h1>
 <h2>气泡</h2>
<Demo :component="popover1Demo" />
<Demo :component="popover2Demo" />
</template>
<script>
import Demo from './Demo.vue'
import popover1Demo from './popover.demo.vue'
import popover2Demo from './popover2.demo.vue'
  export default {
  components: {
    Demo
  },
  setup() {
    return {
    popover1Demo,
    popover2Demo,
    }
  }
  }
</script>
