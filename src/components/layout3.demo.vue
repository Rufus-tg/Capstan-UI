<demo>
布局3
</demo>
<template>
<Layout>
  <Sider class="sider">Sider</Sider>
   <Layout>
     <Header class="fh"> Header </Header>
    <Content  class="content"> content </Content >
    <Footer class="fh"> footer </Footer>
  </Layout>
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
   name: 'GuluL',
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
  background: #bbb;
  min-width: 100px;
}
.layout:first-child{
   display: flex;
    flex-grow: 1;
flex-direction: row !important;
}
</style>