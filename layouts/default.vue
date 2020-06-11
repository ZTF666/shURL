<template>
  <v-app dark>
    <v-footer :fixed="fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      api: 'https://api.shrtco.de/v2/'
    }
  }
}
</script>
