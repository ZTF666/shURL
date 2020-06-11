<template>
  <v-app dark>
    <Toolbar />
    <Footer />
  </v-app>
</template>

<script>
import Toolbar from '../components/ToolBar'
import Footer from '../components/Footer'
export default {
  components: {
    Toolbar,
    Footer
  },
  data() {
    return {
      api: 'https://api.shrtco.de/v2/'
    }
  }
}
</script>
