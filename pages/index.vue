<template>
    <div :class="$style.wrapper">
        <Item title="Mistra AI" logo="mistrai-ai.webp" v-model="mistralAILabel">
            <MistralAI :label="mistralAILabel" />
        </Item>  
        <Item title="ChatGPT" logo="chat-gpt.svg" v-model="chatGPTLabel">
            <ChatGPT :label="chatGPTLabel" />
        </Item>  
        <Item title="Gemini" logo="gemini.png" v-model="geminiLabel">
            <Gemini :label="geminiLabel" />
        </Item>  
    </div>
</template>

<script setup>
const mistralAILabel = ref('Mistral AI Button');
const chatGPTLabel = ref('ChatGPT Button');
const geminiLabel = ref('Gemini Button');
</script>

<style module>
.wrapper {
    display: flex;
    height: 100vh;
}

.wrapper > * {
    flex: 1;
    position: relative;
}

.wrapper > *:not(:last-child) {
    border-right: solid 1px rgba(255,255,255,0.1);
}
</style>