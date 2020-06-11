<template>
  <v-app dark>
    <Toolbar />
    <Content />
    <Footer />
  </v-app>
</template>

<script>
import Toolbar from '../components/ToolBar'
import Footer from '../components/Footer'
import Content from '../components/content'
export default {
  components: {
    Toolbar,
    Footer,
    Content
  },
  data() {
    return {}
  }
}
</script>
