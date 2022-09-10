<demo>
设置间隙
</demo>
<template>
<gridrow class="demoRow" >
  <gridcol span="8">
    <div class="demoCol">8</div>
  </gridcol>
  <gridcol span="8" offset="8">
    <div class="demoCol">8</div>
  </gridcol>
</gridrow>
<gridrow class="demoRow" >
  <gridcol span="6" offset="6">
    <div class="demoCol">6</div>
  </gridcol>
  <gridcol span="6" offset="6">
    <div class="demoCol">6</div>
  </gridcol>
</gridrow>
<gridrow class="demoRow" >
  <gridcol span="4">
    <div class="demoCol">4</div>
  </gridcol>
  <gridcol span="4" offset="4">
    <div class="demoCol">4</div>
  </gridcol>
  <gridcol span="4" offset="8">
    <div class="demoCol">4</div>
  </gridcol>
</gridrow>
<gridrow class="demoRow" >
  <gridcol span="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2" offset="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2" offset="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2" offset="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2">
    <div class="demoCol">2</div>
  </gridcol>
  <gridcol span="2" offset="2">
    <div class="demoCol">2</div>
  </gridcol>
</gridrow>
</template>

<script lang="ts">
import {
  gridcol,
  gridrow
} from "../lib/index";
export default {
  components: {
    gridcol,
  gridrow
  },
  setup() {
    
  }
}
</script>
<style lang="scss" scoped>
.demoRow{
  margin: 10px 0;
}
.demoCol {
  height: 50px;
  border: 1px solid #ccc;
  background: #eee;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>