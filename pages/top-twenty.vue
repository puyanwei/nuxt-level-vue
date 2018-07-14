<template>
    <v-layout column justify-center align-center>
        <v-flex xs12 sm8 md6>
            <v-card>
                <v-card-title class="headline">Movie Night</v-card-title>
                <v-card-text>
                    <p>Top 20 Movies sorted by rating on The Movie Database</p>
                    <ul>
                        <v-list v-for="film in films" :key="film.id">
                            {{ film.title }} - {{ film.rating }}
                        </v-list>
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
            films: [],
        };
    },
    mounted() {
        this.getMovieData();
    },
    methods: {
        getMovieData() {
            const url = `https://api.themoviedb.org/3/movie/top_rated?api_key=${apiKey}&language=en-US&page=1`;
            fetch(url)
                .then((response) => response.json())
                .then((data) => {
                    let obj = {};
                    data.results.map((element) => {
                        this.films.push({
                            title: element.title,
                            rating: element.vote_average,
                        });
                    });
                })
                .catch((err) => console.log(err));
        },
    },
};
</script>
