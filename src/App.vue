<template>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">{{ text }}</button>
    <Block v-if="showBlock" :delay="delay" @end="end" />
    <Result v-if="showResult" :score="score" />
    <Footer />
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';
import Footer from './components/Footer.vue';

export default {
    name: 'App',
    components: { Block, Result, Footer },
    data() {
        return {
            text: 'Test now',
            isPlaying: false,
            showBlock: false,
            showResult: false,
            delay: null,
            score: 0,
            count: 0,
        };
    },
    updated() {
        if (this.count === 0) {
            this.text = 'Test now';
        } else this.text = 'Test again';
    },
    methods: {
        start() {
            this.delay = Math.random() * 3000 + 2000;
            this.isPlaying = true;
            this.showBlock = true;
            this.showResult = false;
        },
        end(reactionTime) {
            if (reactionTime !== 0) {
                this.score = reactionTime;
                this.showBlock = false;
                this.showResult = true;
            }
            this.isPlaying = false;
            this.count++;
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
