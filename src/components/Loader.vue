<template>
    <div class="loader">
        <slot></slot>
        <div class="text">{{ label }}</div>
    </div>
</template>

<script>
export default {
    name: 'Loader',
    props: {
        label: String,
    },
};
</script>

<style scoped lang="scss">
@import '@/style/vars';
.loader {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.9);
    .text {
        text-transform: uppercase;
        color: rgba($brand-color, 0.5);
        letter-spacing: 5px;
    }
}
img {
    width: 250px;
    margin: 1rem 0;
    animation: pulse 1s infinite alternate;
}

@keyframes pulse {
    from {
        transform: scale(1);
    }
    to {
        transform: scale(1.2);
    }
}
</style>
