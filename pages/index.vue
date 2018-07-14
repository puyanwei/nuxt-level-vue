<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">Movie Night</v-card-title>
        <v-card-text>
          <p>Top 10 Movies</p>
          <ul>
              <li>{{ film }}</li>
          </ul>
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
            film: '',
        };
    },
    mounted() {
        this.getMovieData();
    },
    methods: {
        getMovieData() {
            const url = `https://api.themoviedb.org/3/movie/550?api_key=${apiKey}`;
            fetch(url)
                .then((response) => response.json())
                .then((data) => (this.film = data.title))
                .catch((err) => console.log(err));
        },
    },
};
</script>
