<template>
    <div class="container">
        <section class="top-jumbo">
            <Card
                v-for="(film, index) in movies"
                :key="index"
                :details="film"
            />
        </section>
    </div>
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
