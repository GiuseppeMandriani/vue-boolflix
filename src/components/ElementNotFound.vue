<template>
    <section class="notfound">
        <img
            class="notfound"
            :src="require(`@/assets/404.gif`)"
            alt="not found"
        />
        <h2>Nessun Risultato</h2>
    </section>
</template>

<script>
export default {
    name: 'ElementNotFound',
};
</script>

<style lang="scss" scoped>
@import '../style/notFound.scss';
/* @import '@/style/notFound.scss'; // Arch mi da problemi */
</style>
