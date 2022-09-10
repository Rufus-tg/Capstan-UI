<template>
 <h1>Grid 示例</h1>
<Demo :component="grid1Demo" />
<Demo :component="grid2Demo" />
</template>
<script>
import Demo from './Demo.vue'
import grid1Demo from './grid1.demo.vue'
import grid2Demo from './grid2.demo.vue'
  export default {
  components: {
    Demo
  },
  setup() {
    return {
    grid1Demo,
    grid2Demo,
    }
  }
  }
</script>
