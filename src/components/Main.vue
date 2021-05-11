<template>
    <section>
        <ul>
            <li v-for="(film, index) in movies" :key="index" :details="film">
                <Card :details="film" />
            </li>
        </ul>
    </section>
</template>

<script>
import Card from '@/components/Card.vue';
export default {
    name: 'Main',
    components: {
        Card,
    },
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
