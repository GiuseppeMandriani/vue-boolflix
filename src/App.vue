<template>
    <div id="app">
        <!-- HEADER -->
        <div v-if="!loading">
            <Header @performSearch="getData" />
            <!-- MAIN -->
            <Jumbotron :popular="popularList" :indexImg="indexImg" />
            <Content
                :movies="filmList"
                :series="seriesList"
                :popular="popularList"
                :notFoundError="notFoundMovies && notFoundSeries"
                :loader="loaderMovies || loaderSeries || loaderPopular"
            />
        </div>

        <Loader v-else label="Caricamento...">
            <img
                src="https://fontmeme.com/permalink/210512/aeb2e32c106986dd5cd098b29b231779.png"
                alt="netflix-font"
                border="0"
            />
        </Loader>
    </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Jumbotron from '@/components/Jumbotron.vue';
import Content from '@/components/Content.vue';
import Loader from '@/components/Loader.vue';

export default {
    name: 'App',
    components: {
        Header,
        Jumbotron,
        Content,
        Loader,
    },

    data() {
        return {
            filmList: [], // Arr per contenere API film
            seriesList: [], // Arr per contenere API series
            popularList: [],
            urlApi: 'https://api.themoviedb.org/3/search/',
            urlApiPopular: 'https://api.themoviedb.org/3/movie/popular',
            apiKey: 'ad7cef1cdf8a5fcf4e73a44c4f9e4bba',
            loading: true,
            notFoundMovies: false,
            notFoundSeries: false,
            loaderMovies: false,
            loaderSeries: false,
            loaderPopular: false,
            indexImg: 0,
        };
    },

    created() {
        // CALL API POPULAR
        setTimeout(() => {
            this.getPopular();
        }, 2000);
    },

    methods: {
        getData(searchText) {
            console.log(searchText);
            if (searchText !== '') {
                const apiParams = {
                    api_key: this.apiKey,
                    query: searchText,
                    language: 'it-IT',
                };

                // Call API Movies
                axios
                    .get(this.urlApi + 'movie', {
                        params: apiParams,
                    })
                    .then(res => {
                        this.filmList = res.data.results;
                        this.notFoundMovies = this.filmList.length === 0;
                        this.loaderMovies = true;
                    });

                // Call API Series
                axios
                    .get(this.urlApi + 'tv', {
                        params: apiParams,
                    })
                    .then(res => {
                        this.seriesList = res.data.results;
                        this.notFoundSeries = this.seriesList.length === 0;
                        this.loaderSeries = true;
                    });
            } else {
                this.filmList = [];
                this.seriesList = [];
                this.getPopular();
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
                    this.popularList = res.data.results;
                    this.loading = false;
                    this.loaderPopular = true;
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
