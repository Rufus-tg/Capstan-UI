<template>
 <h1>layout 示例</h1>
<Demo :component="layout1Demo" />
<Demo :component="layout2Demo" />
<Demo :component="layout3Demo" />
</template>
<script>
import Demo from './Demo.vue'
import layout1Demo from './layout1.demo.vue'
import layout2Demo from './layout2.demo.vue'
import layout3Demo from './layout3.demo.vue'
  export default {
  components: {
    Demo
  },
  setup() {
    return {
    layout1Demo,
    layout2Demo,
    layout3Demo,
    }
  }
  }
</script>
