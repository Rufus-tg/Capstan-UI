
<demo>
双向绑定
</demo>
<template>
<GP v-model:value="value"></GP>
<p>value: {{value}}</p>
</template>

<script lang="ts">
import GP from "../inp.vue"
export default {
data() {
  
  return {
    value: ''
  };
},
  components: {
  GP
  }, methods:{
      //  oninput(e){
      //    console.log(document.querySelector('#inp').);
         
      //     // this.$emit('input',e.target.value);
      // }
    },
  setup() {
    
  },
}
</script>
<style lang="scss" scoped>

</style>