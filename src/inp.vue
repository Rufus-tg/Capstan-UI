<template>
    <input type="text" :value="value" @input="oninput"/>

</template>
<script>
  export default {
       name: 'GP',
       props:['value'],
    methods:{
      oninput(e){
          console.log(e.target.value);
          this.$emit('update:value',e.target.value);
      }
    }
  }
</script>
<style lang="scss" scoped>
 input{
       padding: 10px;
    outline: none;
    border-radius: 10px;
    margin: 10px;
    
 }
</style>