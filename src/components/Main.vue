<template>
    <section>
        <ul v-for="(film, index) in movies" :key="index">
            <li>{{ film.title }}</li>
            <li>{{ film.original_title }}</li>
            <li>{{ film.original_language }}</li>
            <li>{{ film.vote_average }}</li>
        </ul>
    </section>
</template>

<script>
export default {
    name: 'Main',
    props: {
        movies: Array,
    },
};
</script>

<style lang="scss" scoped>
ul {
    padding: 20px;
}
</style>
