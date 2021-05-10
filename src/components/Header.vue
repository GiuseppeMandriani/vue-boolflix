<template>
    <!-- Logo -->
    <div class="header">
        <div class="nav-left">
            <div class="logo">
                <a href="https://fontmeme.com/netflix-font/"
                    ><img
                        src="https://fontmeme.com/permalink/210510/a43d586dbbb0088129005263a09c8438.png"
                        alt="netflix-font"
                        border="0"
                /></a>
            </div>
        </div>
        <div class="nav-right">
            <form action="">
                <input
                    type="text"
                    placeholder="Search"
                    v-model.trim="searchText"
                />
                <button
                    type="submit"
                    @click.prevent="$emit('performSearch', searchText)"
                >
                    Search
                </button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            searchText: '',
        };
    },
    computed: {
        filterMovies() {
            if (this.searchText === '') {
                return this.filmList;
            }
            return this.filmList.filter(element => {
                return element.title
                    .toLowerCase()
                    .includes(this.searchinMovies);
            });
        },
    },
};
</script>

<style lang="scss" scoped>
.header {
    padding: 20px;
    display: flex;
    justify-content: space-between;
    img {
        width: 200px;
    }
}
</style>
