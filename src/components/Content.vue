<template>
    <div class="container top-jumbo">
        <!-- Element Not Found -->
        <ElementNotFound v-show="notFoundError" />

        <!-- Section Movies -->
        <section v-show="movies.length">
            <h2>Movies</h2>
            <div class="flex">
                <Card
                    v-for="(film, index) in movies"
                    :key="index"
                    :details="film"
                    @indexFilm="setData"
                />
            </div>
        </section>

        <!-- Section Series -->
        <section v-show="series.length" class="list">
            <h2>Serie Tv</h2>
            <div class="flex">
                <Card
                    v-for="serie in series"
                    :key="serie.id"
                    :details="serie"
                    @indexFilm="setData"
                />
            </div>
        </section>

        <!-- Section Popular -->
        <section v-show="popular.length">
            <h2>Popolari</h2>
            <div class="flex ">
                <Card
                    v-for="popolare in popular"
                    :key="popolare.id"
                    :details="popolare"
                    @indexFilm="setData"
                />
            </div>
        </section>
        <section>
            <!-- <Loader label="Caricamento..." :isVisible="LoaderMovies">
                <img
                    src="https://fontmeme.com/permalink/210512/aeb2e32c106986dd5cd098b29b231779.png"
                    alt="netflix-font"
                    border="0"
                />
            </Loader> -->
        </section>
    </div>
</template>

<script>
import Card from '@/components/Card.vue';
// import Loader from '@/components/Loader.vue';
import ElementNotFound from '@/components/ElementNotFound.vue';

export default {
    name: 'Content',
    components: {
        Card,
        ElementNotFound,
    },
    props: {
        movies: Array,
        series: Array,
        popular: Array,
        notFoundError: Boolean,
    },

    methods: {
        // Functions per selezionare il film
        setData(details) {
            console.log('LOG CONTENT', details);
            this.$emit('setImgData', details);
        },
    },
};
</script>

<style scoped lang="scss">
.top-jumbo {
    position: relative;
    margin-top: 1rem;
}
.flex {
    display: flex;
    /* flex-wrap: nowrap; */
    overflow-x: auto;
}

h2 {
    font-size: 2rem;
    color: #fff;
    letter-spacing: 1px;
}
</style>
