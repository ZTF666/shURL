<template>
  <div>
    <v-app-bar absolute color="#fcb69f" dark dense src="https://picsum.photos/1920/1080?random">
      <template v-slot:img="{ props }">
        <v-img v-bind="props" gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"></v-img>
      </template>

      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        src="https://raw.githubusercontent.com/ZTF666/Avatar-Fetcher/master/src/assets/me.png"
        transition="scale-transition"
        width="40"
      />

      <v-toolbar-title>shURL | ショート URL</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon href="#" target="_blank">
        <v-icon>mdi-link</v-icon>
      </v-btn>

      <v-btn icon href="https://github.com/ZTF666/shurl" target="_blank">
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {}
</script>

<style>
</style>