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
        <input :class="$style.input" type="text" v-model="model" placeholder="Libéllé du bouton">
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const model = defineModel()

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

.title {
    font-size: 12px;
    font-weight: 900;
    padding-bottom: 20px;
    border-bottom: solid 1px #ffffff20;
}

.logo {
    height: 50px;
}

.logo img {
    height: 100%;
    color: white;
}
.input {
    position: absolute;
    bottom: 20px;
    left: 10px;
    width: calc(100% - 20px);
    background-color: #1f1f1f;
    padding: 15px;
    border-radius: 5px;
    color: white;
}
</style>