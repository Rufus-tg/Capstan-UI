<template>
 <h1>Input 示例</h1>
 <h2>文本框</h2>
<Demo :component="input1Demo" />
<Demo :component="input2Demo" />
</template>
<script>
import Demo from './Demo.vue'
import input1Demo from './input1.demo.vue'
import input2Demo from './input2.demo.vue'
  export default {
  components: {
    Demo
  },
  setup() {
    return {
    input1Demo,
    input2Demo,
    }
  }
  }
</script>
