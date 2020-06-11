<template>
  <v-app dark>
    <Toolbar />

    <v-footer :fixed="fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import Toolbar from '../components/ToolBar'
export default {
  components: {
    Toolbar
  },
  data() {
    return {
      api: 'https://api.shrtco.de/v2/'
    }
  }
}
</script>
