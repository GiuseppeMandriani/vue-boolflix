<template>
    <div class="item">
        <img
            :src="`https://image.tmdb.org/t/p/w154${details.poster_path}`"
            :alt="`Img of ${details.name} not found`"
        />
        <ul class="list">
            <li v-if="details.title === details.name">
                {{ details.title ? details.title : details.name }}
            </li>
            <li v-else>
                {{
                    details.original_title
                        ? details.original_title
                        : details.original_name
                }}
            </li>
            <li>
                <img
                    v-if="isFlag(details.original_language)"
                    :src="require(`@/assets/${details.original_language}.png`)"
                    :alt="details.original_language"
                />
                <span v-else>{{ details.original_language }}</span>
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
                    v-for="(stars, index) in 5 -
                        Math.round(details.vote_average / 2)"
                    :key="'A' + index"
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
    methods: {
        isFlag(language) {
            return this.flags.includes(language);
        },
    },
};
</script>

<style lang="scss" scoped>
.item {
    flex-basis: calc(100% / 5 - 2rem);
    margin: 1rem 1rem;
}

li img {
    width: 32px;
}
</style>
