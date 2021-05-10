<template>
    <div id="app">
        <!-- HEADER -->
        <Header />

        <!-- MAIN -->
        <main>
            <TopJumbo />
        </main>
    </div>
</template>

<script>
import Header from '@/components/Header';
import TopJumbo from '@/components/TopJumbo';
export default {
    name: 'App',
    components: {
        Header,
        TopJumbo,
    },
};
</script>

<style lang="scss">
@import '~@fontsource/bebas-neue/index.css';
@import '@/style/general.scss';
</style>
