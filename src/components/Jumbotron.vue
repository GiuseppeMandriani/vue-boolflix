<template>
    <section id="jumbo" class="jumbotron container   ">
        <!-- Images Jumbotron -->
        <div class="images ">
            <div class=" card-content ">
                <img
                    v-if="imgDetails.backdrop_path"
                    class="big-img"
                    :src="
                        `https://image.tmdb.org/t/p/w1280${imgDetails.backdrop_path}`
                    "
                    alt=""
                    tabindex="0"
                />
                <img
                    v-else
                    class="poster"
                    src="https://www.altavod.com/assets/images/poster-placeholder.png"
                    alt=""
                />
                <ul class="details-list">
                    <li v-if="imgDetails.title === imgDetails.name">
                        {{
                            imgDetails.title
                                ? imgDetails.title
                                : imgDetails.name
                        }}
                    </li>
                    <li v-else>
                        {{
                            imgDetails.original_title
                                ? imgDetails.original_title
                                : imgDetails.original_name
                        }}
                    </li>
                    <li>
                        <img
                            v-if="isFlag(imgDetails.original_language)"
                            :src="
                                require(`@/assets/${imgDetails.original_language}.png`)
                            "
                            :alt="imgDetails.original_language"
                        />
                        <span v-else>{{ imgDetails.original_language }}</span>
                    </li>
                    <li>{{ imgDetails.overview }}</li>
                    <li>
                        <span
                            class="full-stars"
                            v-for="(stars, index) in Math.round(
                                imgDetails.vote_average / 2
                            )"
                            :key="index"
                        >
                            <i class="fas fa-star"></i> </span
                        ><span
                            class="empty-stars"
                            v-for="(stars, index) in 5 -
                                Math.round(imgDetails.vote_average / 2)"
                            :key="'A' + index"
                            ><i class="fas fa-star"></i>
                        </span>
                    </li>
                </ul>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Jumbotron',
    props: {
        imgDetails: Object,
        popular: Array,
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
@import '@/style/jumbotronStyles.scss';
</style>
