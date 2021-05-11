<template>
    <section class="card">
        <ul>
            <li>{{ details.title }}</li>
            <li>{{ details.original_title }}</li>
            <li>{{ details.original_language }}</li>
            <li>{{ details.vote_average }}</li>
        </ul>
    </section>
</template>

<script>
export default {
    name: 'Card',
    props: {
        details: Object,
    },
};
</script>

<style lang="scss" scoped></style>
