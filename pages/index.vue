<template>
    <div :class="$style.wrapper">
        <Item title="Mistra AI" logo="mistrai-ai.webp">
            <MistralAI />
        </Item>  
        <Item title="ChatGPT" logo="chat-gpt.svg">
            <ChatGPT />
        </Item>  
        <Item title="Gemini" logo="gemini.png">
            <Gemini />
        </Item>  
    </div>
</template>

<style module>
.wrapper {
    display: flex;
    height: 100vh;
}

.wrapper > * {
    flex: 1
}

.wrapper > *:not(:last-child) {
    border-right: solid 1px rgba(255,255,255,0.1);
}
</style>