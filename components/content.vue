<template>
  <div class="mt-10">
    <v-form @submit.prevent="getLyrics()">
      <v-container>
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs8 sm6 md6>
            <v-row>
              <v-col cols="12" sm="6" md="6">
                <v-text-field label="Link" outline v-model="inLink" aria-autocomplete="false"></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="6" class="mt-5">
                <v-btn @click.prevent="getLyrics()">Generate Link</v-btn>
              </v-col>
            </v-row>
            <v-row class="d-flex justify-center">
              <div></div>
            </v-row>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      inLink: '',
      api: 'https://api.shrtco.de/v2/'
    }
  }
}
</script>

<style>
</style>