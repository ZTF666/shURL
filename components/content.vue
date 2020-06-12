<template>
  <div class="mt-10">
    <v-form @submit.prevent="shortenURL()">
      <v-container>
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs8 sm6 md6>
            <v-row class="d-flex justify-center">
              <v-col cols="12" sm="6" md="6">
                <v-text-field label="Link" outline v-model="inLink" aria-autocomplete="false"></v-text-field>
              </v-col>
            </v-row>

            <v-row class="d-flex justify-center">
              <div>
                <v-col cols="12" sm="6" md="6" class="mt-5">
                  <v-btn @click.prevent="shortenURL()">Generate Link</v-btn>
                </v-col>
              </div>
            </v-row>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
    <!-- CONTENT -->

    <v-card max-width="344" class="mx-auto mt-10">
      <v-list-item>
        <!-- <v-list-item-avatar color="grey"></v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-title class>{{msg}}</v-list-item-title>
          <!-- <v-list-item-subtitle>by Kurt Wagner</v-list-item-subtitle> -->
        </v-list-item-content>
      </v-list-item>

      <v-img src="https://picsum.photos/1920/1080?random" height="100"></v-img>

      <v-card-text>{{shurl1}}</v-card-text>
      <v-card-text>{{shurl2}}</v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn icon>
          <v-icon>mdi-floppy</v-icon>
        </v-btn>
      </v-card-actions>
    </v-card>
    <!-- END CONTENT -->
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      inLink: '',
      shurl1: '',
      shurl2: '',
      msg: ''
    }
  },
  methods: {
    async shortenURL() {
      if (this.inLink != null) {
        let response = await axios.get(
          `https://api.shrtco.de/v2/shorten?url=` + this.inLink
        )
        console.log(response.data.ok)
        if (response.data.ok == true) {
          this.shurl1 = response.data.result.short_link
          this.shurl2 = response.data.result.short_link2
          console.log(this.shurl1)
          console.log(this.shurl2)
        }
        // console.log(response.data.result.short_link)
      }
    }
  }
}
</script>

<style></style>
