<template>
    <div class="container top-jumbo">
        <section v-show="movies.length === 0 && series.length === 0">
            <h2>Elemento non trovato</h2>
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
    </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Content',
    components: {
        Card,
    },
    props: {
        movies: Array,
        series: Array,
        popular: Array,
    },
};
</script>

<style scoped lang="scss">
.flex {
    display: flex;
    flex-wrap: wrap;
}
</style>
