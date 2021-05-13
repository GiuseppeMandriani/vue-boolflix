<template>
    <div class="item">
        <div class="img">
            <img
                v-if="details.poster_path"
                :src="`https://image.tmdb.org/t/p/w154${details.poster_path}`"
                :alt="`Img of ${details.name} not found`"
                @click="
                    $emit(
                        'indexFilm',
                        `https://image.tmdb.org/t/p/w154${details.poster_path}`
                    )
                "
            />
            <img
                class="img"
                v-else
                src="https://www.altavod.com/assets/images/poster-placeholder.png"
                alt=""
            />
        </div>
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
                <!-- <i
                    v-for="i in getStarVote(details.vote_average)"
                    :key="`full- ${i}`"
                    class="fas fa-star"
                ></i>
                <i
                    v-for="i in 5 - getStarVote(details.vote_average)"
                    :key="`empty- ${i}`"
                    class="far fa-star"
                ></i> -->

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
        getStarVote(vote) {
            Math.ceil(vote / 2);
        },
    },
};
</script>

<style lang="scss" scoped>
.item {
    flex-basis: calc(100% / 5);
}

li img {
    width: 32px;
}
</style>
