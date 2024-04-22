<script setup lang="ts">
import TheAccordion from '@/components/TheAccordion.vue';
const mobileImage = new URL('../assets/images/background-pattern-mobile.svg', import.meta.url).href;
const desktopImage = new URL('../assets/images/background-pattern-desktop.svg', import.meta.url).href;
</script>

<template>
    <div class="container">
        <div class="decoration">
            <picture>
                <source media="(max-width: 640px)" :srcset="mobileImage">
                <img class="decoration-image" :src="desktopImage" alt="">
            </picture>
        </div>
        <TheAccordion />
    </div>
</template>


<style scoped>
.container {
    display: flex;
    justify-content: center;
    height: 100vh;
    min-height: 100vh;
    padding: 10.5rem 0;
    background-color: var(--light-pink);

    @media screen and (max-width: 640px) {
        padding: 8.875rem 1.5rem;
    }
}

.decoration {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 320px;
}

.decoration-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>