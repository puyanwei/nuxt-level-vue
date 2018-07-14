<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">Movie Night</v-card-title>
        <v-card-text>
          <p>Top 10 Movies</p>
          <div class="text-xs-right">
          </div>
          <hr class="my-3">
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import { apiKey } from '../utils/api-key';

export default {
    data() {
        return {
            apiKey: '',
        };
    },
    mounted() {
        this.getMovieData();
    },
    methods: {
        getMovieData() {
            // const url = `http://api.giphy.com/v1/gifs/search?q=random+${query}&api_key=${giffyAPI}&limit=50`;
            // const response = await fetch(url);
            // const giffyData = await response.json();
            // return giffyId;
            console.log(apiKey);
        },
    },
};
</script>
