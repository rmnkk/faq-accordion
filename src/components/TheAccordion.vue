<script setup lang="ts">
import TheAccordionSection from '@/components/TheAccordionSection.vue';

const iconStar = new URL('../assets/images/icon-star.svg', import.meta.url).href;
const accordionData = [
    {
        title: `What is Frontend Mentor, and how will it help me?`,
        content: `Frontend Mentor offers realistic coding challenges to help developers
             improve their frontend coding skills with projects in HTML, CSS, and JavaScript.
                It's suitable for all levels and ideal for portfolio building.
        `
    },
    {
        title: `Is Frontend Mentor free?`,
        content: `Yes, Frontend Mentor offers both free and premium coding challenges, with the free 
  option providing access to a range of projects suitable for all skill levels.`
    },
    {
        title: `Can I use Frontend Mentor projects in my portfolio?`,
        content: `Yes, you can use projects completed on Frontend Mentor in your portfolio. It's an excellent
  way to showcase your skills to potential employers!`
    },
    {
        title: `How can I get help if I'm stuck on a challenge?`,
        content: `The best place to get help is inside Frontend Mentor's Discord community. There's a help 
  channel where you can ask questions and seek support from other community members.`
    }
]
</script>

<template>
    <div class="accordion">
        <div class="header">
            <img class="icon" :src="iconStar">

            <h2 class="title">
                FAQs
            </h2>
        </div>

        <div>
            <TheAccordionSection v-for="(section, index) in accordionData" :key="section.title" :index="index">
                <template #title>
                    {{ section.title }}
                </template>

                <template #content>
                    {{ section.content }}
                </template>
            </TheAccordionSection>
        </div>
    </div>
</template>

<style scoped>
.accordion {
    width: 100%;
    max-width: 600px;
    height: fit-content;
    padding: 2.5rem;
    background-color: #fff;
    border-radius: 1rem;
    z-index: 1;

    @media screen and (max-width: 640px) {
        padding: 1.5rem;
    }
}

.header {
    display: flex;
    align-items: center;
    margin-bottom: 2rem;

    @media screen and (max-width: 640px) {
        margin-bottom: 1.5rem;
    }
}

.title {
    margin-left: 1.5rem;
    font-size: 3.5rem;
    font-weight: 700;
    color: var(--dark-purple);

    @media screen and (max-width: 640px) {
        font-size: 2rem;
    }
}
</style>