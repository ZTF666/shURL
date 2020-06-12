<template>
  <div class="mt-10">
    <v-form @submit.prevent="shortenURL()">
      <v-container>
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs8 sm6 md6>
            <v-row class="d-flex justify-center">
              <v-col cols="12" sm="6" md="6">
                <v-text-field
                  label="Link"
                  outline
                  v-model="inLink"
                  required
                ></v-text-field>
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

    <v-card max-width="800" class="mx-auto mt-10">
      <v-list-item>
        <!-- <v-list-item-avatar color="grey"> -->
        <!-- <v-img :src="img"></v-img> -->
        <!-- </v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-text class="justify-center"
            ><div>
              <h1 class="headline text-md-center">{{ msg }}</h1>
            </div></v-list-item-text
          >
          <!-- <v-list-item-subtitle>by Kurt Wagner</v-list-item-subtitle> -->
        </v-list-item-content>
      </v-list-item>

      <v-img :src="img" height="400"></v-img>

      <v-card-text class="justify-center">
        <div>
          <h4 class="headline text-md-center">{{ shurl }}</h4>
        </div>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <!-- <v-btn text >
          <v-icon>mdi-floppy</v-icon>
        </v-btn> -->
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
      shurl: '',
      msg: '',
      img: 'https://picsum.photos/1920/1080?random'
    }
  },
  methods: {
    async shortenURL() {
      try {
        if (this.inLink != '') {
          this.msg = 'Your link is being processed ...'
          let response = await axios.get(
            `https://api.shrtco.de/v2/shorten?url=` + this.inLink
          )

          console.log(response.status)
          if (response.data.ok == true) {
            this.shurl = response.data.result.short_link
            this.msg = 'Your link is ready !'
            console.log(this.shurl)
          }
        }
        if (this.inLink == '') {
          this.msg = 'Please paste a link'
        }
      } catch (e) {
        this.shurl =
          'Sorry an error has occured , link disallowed or unknown error please retry '
      }
    }
  }
}
</script>

<style></style>
