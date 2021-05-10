<template>
    <div id="app">
        <!-- HEADER -->
        <Header @performSearch="getFilmList" />

        <!-- MAIN -->
        <Main :movies="filmList" />
    </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';
export default {
    name: 'App',
    components: {
        Header,
        Main,
    },

    data() {
        return {
            urlApi: 'https://api.themoviedb.org/3/search/movie',
            filmList: [], // Arr per contenere API
            searchinMovies: '',
        };
    },

    methods: {
        getFilmList(element) {
            // CALL
            axios
                .get(this.urlApi, {
                    params: {
                        api_key: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
                        query: element,
                        language: 'it-IT',
                    },
                })
                .then(res => {
                    console.log(res.data.results);
                    this.filmList = res.data.results;
                })
                .catch(err => {
                    console.log('Errore', err);
                });
        },

        searchElement(text) {
            this.searchinMovies = text;
        },
    },
};
</script>

<style lang="scss">
@import '~@fontsource/bebas-neue/index.css';
@import '@/style/general.scss';
</style>
