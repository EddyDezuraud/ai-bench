<template>
    <div :class="$style.wrapper">
        <div :class="$style.logo">
            <img :src="logo" />
        </div>
        <div :class="$style.title">
            <span>{{ title }}</span>
        </div>
        <div :class="$style.content">
            <slot></slot>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    title: String,
    logo: String
})
</script>

<style module>
.wrapper {
   display: flex;
   flex-direction: column;
   align-items: center;
   gap: 30px;
   padding: 80px 20px;
}

.logo {
    height: 50px;
}

.logo img {
    height: 100%;
    color: white;
}
</style>