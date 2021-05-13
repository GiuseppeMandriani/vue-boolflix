<template>
    <section class="notfound">
        <img
            class="notfound"
            :src="require(`@/assets/404.gif`)"
            alt="not found"
        />
    </section>
</template>

<script>
export default {
    name: 'ElementNotFound',
};
</script>

<style lang="scss" scoped>
@import '@/style/notfound.scss';
</style>
