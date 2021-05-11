<template>
    <!-- Logo -->
    <div class="header container">
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
            <form>
                <input
                    type="text"
                    placeholder="Search your film/serie Tv here ..."
                    v-model.trim="searchText"
                    @keyup="$emit('performSearch', searchText)"
                />
                <button
                    class="btn-search"
                    type="submit"
                    @click.prevent="$emit('performSearch', searchText)"
                >
                    <i class="fas fa-search"></i>
                </button>
                <button class="btn-reset" type="reset">
                    <i class="fas fa-backspace"></i>
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
        // filterMovies() {
        //     if (this.searchText === '') {
        //         return this.filmList;
        //     }
        //     return this.filmList.filter(element => {
        //         return element.title
        //             .toLowerCase()
        //             .includes(this.searchinMovies);
        //     });
        // },
    },
};
</script>

<style lang="scss" scoped>
.header {
    height: 80px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    img {
        width: 200px;
    }
}

.nav-right {
    input {
        width: 250px;
        padding: 10px;
        margin-right: 1rem;
        outline: none;
        border: none;
        &:focus {
            border: 1px solid #ccc;
        }
    }
    button.btn-search,
    button.btn-reset {
        padding: 10px;
        background: transparent;
        border: none;
        font-size: 1.2rem;
        cursor: pointer;
    }
}
</style>
