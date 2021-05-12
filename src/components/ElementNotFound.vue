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
.notfound {
    text-align: center;
    img {
        width: 200px;
    }
}
</style>
