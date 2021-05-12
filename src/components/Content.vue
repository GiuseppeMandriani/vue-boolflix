<template>
    <div class="container top-jumbo">
        <section v-show="notFoundError" class="notfound">
            <img
                class="notfound"
                :src="require(`@/assets/404.gif`)"
                alt="not found"
            />
        </section>
        <section v-show="movies.length" class="list">
            <h2>Movies</h2>
            <div class="flex">
                <Card v-for="film in movies" :key="film.id" :details="film" />
            </div>
        </section>
        <section v-show="series.length" class="list">
            <h2>Serie Tv</h2>
            <div class="flex">
                <Card
                    v-for="serie in series"
                    :key="serie.id"
                    :details="serie"
                />
            </div>
        </section>
        <section v-show="popular.length" class="list">
            <h2>Popolari</h2>
            <div class="flex">
                <Card
                    v-for="popolare in popular"
                    :key="popolare.id"
                    :details="popolare"
                />
            </div>
        </section>
        <section v-show="loader">
            <Loader label="Caricamento...">
                <img
                    src="https://fontmeme.com/permalink/210512/aeb2e32c106986dd5cd098b29b231779.png"
                    alt="netflix-font"
                    border="0"
                />
            </Loader>
        </section>
    </div>
</template>

<script>
import Card from '@/components/Card.vue';
import Loader from '@/components/Loader.vue';

export default {
    name: 'Content',
    components: {
        Card,
        Loader,
    },
    props: {
        movies: Array,
        series: Array,
        popular: Array,
        notFoundError: Boolean,
        loader: Boolean,
    },
};
</script>

<style scoped lang="scss">
.flex {
    display: flex;
    flex-wrap: wrap;
}
.notfound {
    text-align: center;
    img {
        width: 200px;
    }
}
</style>
