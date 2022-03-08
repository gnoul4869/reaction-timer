<template>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Test now</button>
    <Block v-if="isPlaying" :delay="delay" @end="end" />
    <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';
export default {
    name: 'App',
    components: { Block, Result },
    data() {
        return {
            isPlaying: false,
            showResult: false,
            delay: null,
            score: 0,
        };
    },
    methods: {
        start() {
            this.delay = Math.random() * 3000 + 2000;
            this.isPlaying = true;
            this.showResult = false;
        },
        end(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            this.showResult = true;
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #444;
    margin-top: 3.75rem;
}
button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 0.25rem;
    font-size: 1rem;
    letter-spacing: 0.0625rem;
    cursor: pointer;
    margin: 3.125rem;
}
button[disabled] {
    opacity: 0.5;
    cursor: not-allowed;
}
</style>
