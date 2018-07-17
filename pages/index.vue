<template>
    <div class="movie-search">
        <h1>Movie Night</h1>
        <p>Find a Movie</p>
        <v-text-field placeholder="Search Movies" v-model="userInput" v-on:keyup="getMovieData" ></v-text-field>
        <div style="position:relative">
            <ul class="dropdown-menu">
                <li v-for="film in getMovieData" :key="film.id">
                    <a href="#" style="color:white">{{ film }}</a>
                </li>
            </ul>
        </div>
    </div>
</template>



<script>
import { apiKey } from '../utils/api-key';

export default {
    data() {
        return {
            userInput: '',
            films: [
                'Fight Club',
                'Pulp Fiction',
                'Shawshank Redemption',
                'Life of Pi',
                'Ready Player One',
                'Jurassic Park',
            ],
            openBox: false,
        };
    },
    // computed: {
    //     suggestedFilms() {
    //         return this.films.filter((element) => {
    //             return element
    //                 .toLowerCase()
    //                 .match(this.userInput.toLowerCase());
    //         });
    //     },
    // },
    methods: {
        getMovieData() {
            console.log('called');
            const url = `https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${
                this.userInput
            }`;
            fetch(url)
                .then((response) => response.json())
                .then((data) => {
                    console.log(data);
                })
                .catch((err) => console.log(err));
            return this.films;
        },
    },
    // openSuggestionBox() {
    //     return (
    //         this.selection !== '' &&
    //         this.matches.length != 0 &&
    //         this.openBox === true
    //     );
    // },
    // },
    // methods: {
};
</script>
