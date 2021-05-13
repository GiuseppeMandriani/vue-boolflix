<template>
    <div class="item">
        <div class="card-content">
            <img
                class="poster"
                v-if="details.poster_path"
                :src="
                    `https://image.tmdb.org/t/p/original${details.poster_path}`
                "
                :alt="`Img of ${details.name} not found`"
            />
            <!-- <img
                class="poster"
                v-else
                src="https://www.altavod.com/assets/images/poster-placeholder.png"
                alt=""
            /> -->

            <ul class="details-list" @click="$emit('indexFilm', details)">
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
                        :src="
                            require(`@/assets/${details.original_language}.png`)
                        "
                        :alt="details.original_language"
                    />
                    <span v-else>{{ details.original_language }}</span>
                </li>
                <li>
                    <span
                        class="full-stars"
                        v-for="(stars, index) in Math.round(
                            details.vote_average / 2
                        )"
                        :key="index"
                    >
                        <i class="fas fa-star"></i> </span
                    ><span
                        class="empty-stars"
                        v-for="(stars, index) in 5 -
                            Math.round(details.vote_average / 2)"
                        :key="'A' + index"
                    >
                    </span>
                </li>
            </ul>
        </div>
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
@import '@/style/card.scss';
</style>
