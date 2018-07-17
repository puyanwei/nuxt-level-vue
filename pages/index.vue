<template>
    <div class="movie-search">
        <h1>Movie Night</h1>
        <p>Find a Movie</p>
        <v-text-field placeholder="Search Movies" v-model="userInput" ></v-text-field>
        <div style="position:relative">
            <ul class="dropdown-menu">
                <li v-for="film in suggestedFilms" :key="film.id">
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
    computed: {
        suggestedFilms() {
            return this.films.filter((element) => {
                return element
                    .toLowerCase()
                    .match(this.userInput.toLowerCase());
            });
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
    //     getMovieData(search) {
    //         const url = `https://api.themoviedb.org/3/search/${search}?api_key=${apiKey}&language=en-US&page=1&include_adult=false`;
    //         fetch(url)
    //             .then((response) => response.json())
    //             .then((data) => {
    //                 console.log(data);
    //             })
    //             .catch((err) => console.log(err));
    //     },
    // },
};
</script>
