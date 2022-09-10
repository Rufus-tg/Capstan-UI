<template>
 <h1>Collapse 示例</h1>
 <h2>手风琴</h2>
<Demo :component="collapse1Demo" />
<Demo :component="collapse2Demo" />
</template>
<script>
import Demo from './Demo.vue'
import collapse1Demo from './collapse1.demo.vue'
import collapse2Demo from './collapse2.demo.vue'
  export default {
  components: {
    Demo
  },
  setup() {
    return {
    collapse1Demo,
    collapse2Demo,
    }
  }
  }
</script>
