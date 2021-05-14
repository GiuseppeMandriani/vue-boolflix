<template>
    <section class="start">
        <h2>benvenuto scegli cosa guardare</h2>
    </section>
</template>

<script>
export default {
    name: 'Start',
};
</script>

<style lang="scss" scoped>
@import '@/style/vars.scss';
.start {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    h2 {
        font-size: 4.5rem;
        letter-spacing: 3px;
        color: rgba($brand-color, 0.6);
        font-weight: 400;
    }
}
</style>
