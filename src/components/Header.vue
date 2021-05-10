<template>
    <header class="header-content container">
        <!-- BRAND LOGO -->
        <div class="nav-left">
            <a href="https://fontmeme.com/netflix-font/"
                ><img
                    src="https://fontmeme.com/permalink/210510/a43d586dbbb0088129005263a09c8438.png"
                    alt="netflix-font"
                    border="0"
            /></a>
            <!-- <ul class="menu-search">
                <li><a href="#">Home</a></li>
                <li><a href="#">Film</a></li>
                <li><a href="#">Serie TV</a></li>
                <li><a href="#">La mia lista</a></li>
            </ul> -->
        </div>
        <div class="nav-right">
            <div class="searchBox">
                <form>
                    <div>
                        <input
                            type="text"
                            placeholder="Search your title here..."
                        />
                    </div>
                </form>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Headers',
};
</script>

<style lang="scss" scoped>
.header-content {
    height: 80px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
// Brand Logo
.nav-left img {
    width: 180px;
}
</style>
