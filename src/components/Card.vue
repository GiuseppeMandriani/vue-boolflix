<template>
    <div class="item">
        <ul class="list">
            <li>{{ details.title }}</li>
            <li>{{ details.original_title }}</li>
            <li v-if="!flags.includes(details.original_language)">
                {{ details.original_language }}
            </li>
            <li v-else>
                <img
                    :src="require(`../assets/${details.original_language}.png`)"
                    alt=""
                />
            </li>
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
    data() {
        return {
            flags: ['it', 'en'],
        };
    },
};
</script>

<style lang="scss" scoped>
.item {
    flex-basis: calc(100% / 5 - 2rem);
    margin: 1rem 1rem;
}

.list img {
    width: 25px;
}
</style>
