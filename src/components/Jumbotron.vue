<template>
    <section class="jumbotron container ">
        <!-- Images Jumbotron -->
        <div class="images">
            <img :src="imgDetails" alt="" />
        </div>
    </section>
</template>

<script>
export default {
    name: 'Jumbotron',
    props: {
        imgDetails: String,
    },
};
</script>

<style lang="scss" scoped>
@import '@/style/jumbotronStyles.scss';
</style>
