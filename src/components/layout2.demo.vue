<demo>
布局2
</demo>
<template>
<Layout>
  <Header class="fh"> Header </Header>
  <Layout>
    <Sider class="sider">Sider</Sider>
    <Content  class="content"> content </Content >
  </Layout>
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
.sider {
  height: 100px;
  background: #bbb;
  min-width: 100px;
  color: black;
}
.fh+.layout{
   display: flex;
    flex-grow: 1;
flex-direction: row !important;
}
</style>