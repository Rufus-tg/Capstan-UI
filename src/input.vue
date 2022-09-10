<template>
    <input ref="input" :value="value" type="text" :disabled="disabled" :readonly="readonly"
      @change="$emit('change', $event.target.value)"
      @input="$emit('input', $event.target.value)"
      @focus="$emit('focus', $event.target.value)"
      @blur="$emit('blur', $event.target.value)"
    >
    <template v-if="error">
      <icon name="error" class="icon-error"></icon>
      <span class="errorMessage">{{error}}</span>
    </template>

</template>
<script>
  import Icon from './icon.vue'
  export default {
    components: {Icon},
    name: 'GuluInput',
    props: {
      value: {
        type: [String, Date]
      },
      disabled: {
        type: Boolean,
        default: false
      },
      readonly: {
        type: Boolean,
        default: false
      },
      error: {
        type: String
      }
    },
    methods:{
      setRawValue(value){
        this.$refs.input.value = value
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
input:not(:nth-child(4)){display: block;}
</style>