<template>
    <section class="jumbotron container ">
        <!-- Images Jumbotron -->
        <div class="images">
            <div class=" big-card img">
                <img
                    :src="
                        `https://image.tmdb.org/t/p/original${imgDetails.poster_path}`
                    "
                    alt=""
                />
            </div>
            <h2>{{ imgDetails.title }}</h2>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Jumbotron',
    props: {
        imgDetails: Object,
        popular: Array,
    },
};
</script>

<style lang="scss" scoped>
@import '@/style/jumbotronStyles.scss';
</style>
