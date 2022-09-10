<template>
  <div class="g-collapse">
      <slot></slot>
  </div>
</template>

<script>
export default {
  components:{},
  props:{
      single: {
          type: Boolean,
          default: false
      },
      selected: {
          type: String
      }
  },
  provide(){
      return { eventBus: this.eventBus}
  },
  mounted(){
    //   this.eventBus.$emit('update:selected', this.selected);
    //   this.eventBus.$on('update:selected', (name)=> {
    //       this.$emit('update:selected', name);
    //   })
    //   this.$children.forEach(vm => {
    //       vm.single = this.single;
    //   });
  }
}
</script>
<style scoped lang='scss'>
.g-collapse {
    border: 1px solid #ddd;
    border-radius: 4px;
}
</style>
