<template>
    <section class="top-jumbo container">
        <h2>Results</h2>

        <ul>
            <li v-for="(film, index) in filmList" :key="index">
                <h3>{{ film.title }}</h3>
                <h3>{{ film.original_title }}</h3>
                <h3>{{ film.original_language }}</h3>
                <h3>{{ film.vote_average }}</h3>

                <!-- <p>{{ film.overview }}</p> -->
            </li>
        </ul>
    </section>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Top-Jumbo',
    data() {
        return {
            urlAPI: 'https://api.themoviedb.org/3/search/movie', // API
            filmList: [], // Array che ospiterà API
        };
    },

    created() {
        this.getFilmList();
    },

    methods: {
        getFilmList() {
            // API CALL
            axios
                .get(this.urlAPI, {
                    params: {
                        api_key: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
                        query: 'iron man',
                    },
                })
                .then(res => {
                    console.log(res.data.results);
                    this.filmList = res.data.results;
                    console.log(this.filmList);
                })
                .catch(err => {
                    console.log('Errore', err);
                });
        },
    },
};
</script>

<style></style>
