<demo>
布局1
</demo>
<template>
<Layout>
  <Header class="fh"> Header </Header>
  <Content  class="content"> content </Content >
  <Footer class="fh"> footer </Footer>
</Layout>
</template>

<script lang="ts">
import {
  Layout,
  Sider,
  Header,
  Footer,
  Content
} from "../lib/index";
export default {
  components: {
    Layout,
    Sider,
  Header,
  Footer,
  Content
  },
  setup() {
    
  }
}
</script>
<style lang="scss" scoped>
.fh {
  height: 50px;
  background: #d3dce6;
}
.content {
  height: 100px;
  background: #99a9bf;
}
</style>