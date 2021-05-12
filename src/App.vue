<template>
    <div id="app">
        <div v-if="!loading">
            <!-- HEADER -->
            <Header @performSearch="getFilmList" @deleteAll="getPopular" />

            <!-- MAIN -->
            <Jumbotron />
            <Main :movies="filmList.concat(seriesList)" />
        </div>

        <Loader v-else label="Caricamento...">
            <img
                src="https://fontmeme.com/permalink/210512/aeb2e32c106986dd5cd098b29b231779.png"
                alt="netflix-font"
                border="0"
            />
        </Loader>
        <NotFound v-show="nessunRisultato" />
    </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Jumbotron from '@/components/Jumbotron.vue';
import Main from '@/components/Main.vue';
import Loader from '@/components/Loader.vue';
import NotFound from '@/components/NotFound.vue';
export default {
    name: 'App',
    components: {
        Header,
        Jumbotron,
        Main,
        Loader,
        NotFound,
    },

    data() {
        return {
            urlApiFilm: 'https://api.themoviedb.org/3/search/movie',
            urlApiSeries: 'https://api.themoviedb.org/3/search/tv',
            urlApiPopular: 'https://api.themoviedb.org/3/movie/popular',
            filmList: [], // Arr per contenere API film
            seriesList: [], // Arr per contenere API series
            loading: true,
            nessunRisultato: [],
        };
    },
    created() {
        // CALL API POPULAR
        setTimeout(() => {
            this.getPopular();
        }, 2000);
    },

    methods: {
        getFilmList(element) {
            if (element === '') {
                // CALL API POPULAR

                this.getPopular();
            } else {
                // CALL API FILM
                axios
                    .get(this.urlApiFilm, {
                        params: {
                            api_key: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
                            query: element,
                            language: 'it-IT',
                        },
                    })
                    .then(res => {
                        console.log('Nessun risultato', res.data.results);
                        this.nessunRisultato = res.data.results;
                        this.filmList = res.data.results;
                        this.loading = false;
                    })
                    .catch(err => {
                        console.log('Errore', err);
                    });

                // CALL API SERIES

                axios
                    .get(this.urlApiSeries, {
                        params: {
                            api_key: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
                            query: element,
                            language: 'it-IT',
                        },
                    })
                    .then(res => {
                        console.log(res.data.results);
                        this.seriesList = res.data.results;
                        this.loading = false;
                    })
                    .catch(err => {
                        console.log('Errore', err);
                    });
            }
        },

        getPopular() {
            // CALL API POPULAR
            axios
                .get(this.urlApiPopular, {
                    params: {
                        api_key: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
                        language: 'it-IT',
                    },
                })
                .then(res => {
                    console.log(res.data.results);
                    this.filmList = res.data.results;
                    this.loading = false;
                })
                .catch(err => {
                    console.log('Errore', err);
                });
        },
    },
};
</script>

<style lang="scss">
@import '~@fontsource/bebas-neue/index.css';
@import '@/style/general.scss';
</style>
