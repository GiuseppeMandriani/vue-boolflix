<template>
    <section>
        <form>
            <div class="nav-right-content">
                <div>
                    <input
                        type="text"
                        placeholder="Search your title here..."
                        v-model.trim="searchText"
                    />
                </div>

                <div class="btn">
                    <button
                        type="submit"
                        @click.prevent="$emit('performSearch', searchText)"
                    >
                        <i class="fas fa-search"></i>
                    </button>
                </div>
                <div class="btn">
                    <button type="reset" @click="resetSearch">
                        <i class="fas fa-backspace"></i>
                    </button>
                </div>
            </div>
        </form>
    </section>
</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
            searchText: '',
        };
    },
    methods: {
        searchFilm(text) {
            this.searchText = text;
            console.log(this.searchText);
        },
        resetSearch() {
            this.searchText = '';
            this.searchFilm(this.searchText);
        },
    },
};
</script>

<style></style>
