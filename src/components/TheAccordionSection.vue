<script setup lang="ts">
import { ref } from 'vue';

defineProps<{
    index: Number,
}>();

const iconMinus = new URL('../assets/images/icon-minus.svg', import.meta.url).href;
const iconPlus = new URL('../assets/images/icon-plus.svg', import.meta.url).href;
const isSectionExpanded = ref(false);
</script>

<template>
    <div class="accordion-item">
        <h3>
            <button type="button" aria-expanded="true" class="trigger" :aria-controls="`section${index}`"
                :id="`accordion${index}`" @click="isSectionExpanded = !isSectionExpanded">

                <span class="title">
                    <slot name="title"></slot>
                </span>

                <img class="icon" :src="isSectionExpanded ? iconMinus : iconPlus" alt="icon">
            </button>
        </h3>

        <Transition name="slide-fade">
            <div v-show="isSectionExpanded" :id="`section${index}`" role="region" :aria-labelledby="`accordion${index}`"
                class="section">
                <p class="content">
                    <slot name="content"></slot>
                </p>
            </div>
        </Transition>
    </div>
</template>


<style scoped>
.accordion-item {
    padding: 1.5rem 0;

    @media screen and (max-width: 640px) {
        padding: 1.25rem 0;
    }
}

.accordion-item:first-child {
    padding-top: 0;
}

.accordion-item:last-child {
    padding-bottom: 0;
}

.accordion-item:not(:last-child) {
    border-bottom: 1px solid var(--light-pink);
}

.trigger {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0;
    font-family: inherit;
    border: none;
    background: #fff;
    cursor: pointer;
}

.title {
    font-size: 1.125rem;
    font-weight: 600;
    color: var(--dark-purple);
    text-align: left;

    @media screen and (max-width: 640px) {
        font-size: 1rem;
    }
}

.title:hover {
    color: var(--pink);
}

.section {
    margin-top: 1.5rem;
}

.content {
    color: var(--pale-purple);

    @media screen and (max-width: 640px) {
        font-size: 0.875rem;
    }
}

.slide-fade-enter-active {
    transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
    transition: all 0.4s ease-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateY(-100%);
    opacity: 0;
}
</style>