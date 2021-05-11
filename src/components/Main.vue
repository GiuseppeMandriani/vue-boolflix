<template>
    <section class="top-jumbo container">
        <Card v-for="(film, index) in movies" :key="index" :details="film" />
    </section>
</template>

<script>
import Card from '@/components/Card.vue';
export default {
    name: 'Main',
    components: {
        Card,
    },
    props: ['movies'],
};
</script>

<style lang="scss" scoped>
.top-jumbo {
    display: flex;
    flex-wrap: wrap;
}
</style>
