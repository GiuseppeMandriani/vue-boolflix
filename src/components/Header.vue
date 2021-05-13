<template>
    <!-- Logo -->
    <div class="header ">
        <div class="position container">
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
                        class="text"
                        :class="{ in: iconStatus, out: iconStatus == false }"
                        type="text"
                        placeholder="Search your film/Serie Tv here ..."
                        v-model.trim="searchText"
                    />
                    <!-- Capire limite chiamate API -->
                    <button
                        @click="clickSearch"
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
    </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            searchText: '',
            iconStatus: undefined,
        };
    },
    methods: {
        clickSearch() {
            this.iconStatus = !this.iconStatus;
        },
    },
};
</script>

<style lang="scss" scoped>
@import '@/style/header.scss';
</style>
