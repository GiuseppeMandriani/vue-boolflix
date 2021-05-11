<template>
    <div class="item">
        <ul class="list">
            <li>{{ details.title }}</li>
            <li>{{ details.original_title }}</li>
            <li>{{ details.original_language }}</li>
            <li>{{ details.vote_average }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        details: Object,
    },
};
</script>

<style lang="scss" scoped>
.item {
    flex-basis: calc(100% / 5 - 2rem);
    margin: 1rem 1rem;
}
</style>
