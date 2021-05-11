<template>
    <div class="item">
        <img
            :src="`https://image.tmdb.org/t/p/w154${details.poster_path}`"
            :alt="`Img of ${details.name} not found`"
        />
        <ul class="list">
            <li>
                Titolo:
                {{ details.title == null ? details.name : details.title }}
            </li>
            <li>
                {{
                    details.original_title == null
                        ? details.original_name
                        : details.original_title
                }}
            </li>
            <li v-if="!flags.includes(details.original_language)">
                {{ details.original_language }}
            </li>
            <li v-else>
                <img
                    :src="require(`../assets/${details.original_language}.png`)"
                    alt=""
                />
            </li>
            <li>
                <span
                    v-for="(stars, index) in Math.round(
                        details.vote_average / 2
                    )"
                    :key="index"
                >
                    <i class="fas fa-star"></i> </span
                ><span
                    v-for="(stars, i) in 5 -
                        Math.round(details.vote_average / 2)"
                    :key="i"
                    ><i class="far fa-star"></i>
                </span>
            </li>
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
    img {
        max-width: 100%;
    }
}

.list img {
    width: 25px;
}
</style>
