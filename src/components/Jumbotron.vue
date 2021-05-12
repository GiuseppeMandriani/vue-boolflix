<template>
    <section class="jumbotron ">
        <section class="slider container">
            <!-- Arrow-left -->
            <div class="prev">
                <i class="fas fa-chevron-left"></i>
            </div>

            <!-- Images Slider -->
            <div class="images">
                <img
                    v-for="(film, indexImg) in popular"
                    :key="indexImg"
                    :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`"
                />
            </div>

            <!-- Arrow-right -->
            <div class="next">
                <i class="fas fa-chevron-right"></i>
            </div>
        </section>
        <!-- <div>
            <ul>
                <li v-for="film in popular" :key="film.id">
                    <img
                        :src="
                            `https://image.tmdb.org/t/p/w342${film.poster_path}`
                        "
                        alt=""
                    />
                </li>
            </ul>
        </div> -->
    </section>
</template>

<script>
export default {
    name: 'Jumbotron',
    props: {
        popular: Array,
        indexImg: Number,
    },
};
</script>

<style lang="scss" scoped>
.jumbotron {
    width: 100%;
    /* height: 300px; */
}
.images {
    /* padding: 20px; */
    display: flex;
    flex-wrap: nowrap;
    overflow-x: hidden;
}
/* Arrows */
.prev,
.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    text-align: center;
    line-height: 50px;
    font-size: 25px;
    color: rgba(255, 255, 255, 0.5);
    cursor: pointer;
    transition: all 0.4s;
    width: 50px;
    height: 50px;
    background-color: rgba(0, 0, 0, 0.7);
    border-radius: 50%;
}

.prev {
    left: 200px;
}

.next {
    right: 200px;
}

.prev:hover,
.next:hover {
    color: #fff;
    background-color: rgba(0, 0, 0, 1);
}

/* ul {
    max-width: 100%;
    display: flex;
    overflow-x: hidden;
} */
</style>
