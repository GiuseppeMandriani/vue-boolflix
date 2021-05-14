<template>
    <div class="container top-jumbo">
        <!-- Element Not Found -->
        <ElementNotFound v-show="notFoundError" />

        <!-- Section Movies -->
        <section v-show="movies.length" class="list">
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

        <!-- Start -->
        <Start v-show="imgDefault" />

        <!-- Section Popular -->
        <section v-show="popular.length" class="list">
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
    </div>
</template>

<script>
import Card from '@/components/Card.vue';

import ElementNotFound from '@/components/ElementNotFound.vue';
import Start from '@/components/Start.vue';

export default {
    name: 'Content',
    components: {
        Card,
        ElementNotFound,
        Start,
    },
    props: {
        movies: Array,
        series: Array,
        popular: Array,
        notFoundError: Boolean,
        imgDefault: Boolean,
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
    /* position: relative; */
    margin-top: 1rem;
}
/* .list {
    margin-bottom: 1rem;
} */
.flex {
    display: flex;
    /* flex-wrap: nowrap; */
    overflow-x: auto;
    overflow-y: hidden;
    --scrollbarBG: #090a0a;
    --thumbBG: #942c06;
    scrollbar-width: thin;
    scrollbar-color: var(--thumbBG) var(--scrollbarBG);
    &::-webkit-scrollbar-thumb {
        background-color: var(--thumbBG);
        border: 3px solid var(--scrollbarBG);
        border-radius: 10px;
    }
    &::-webkit-scrollbar-track {
        background: var(--scrollbarBG);
        border-radius: 10px;
    }
    &::-webkit-scrollbar {
        width: 10px;
        border-radius: 10px;
    }
}

h2 {
    font-size: 2rem;
    color: #fff;
    letter-spacing: 1px;
    margin: 1rem 0;
    letter-spacing: 2px;
}

@media screen and (max-width: 1024px) {
    .flex {
        flex-wrap: wrap;
    }
}
</style>
