<template>
  <svg class="icon"><use :xlink:href="`#i-${name}`"></use></svg>
</template>

<script>
import './assets/svg'
export default {
  props: ["name"],
};
</script>
<style scoped>
.icon {
  width: 1em;
  height: 1em;
  margin: 0px 0.1em;
}
</style>
