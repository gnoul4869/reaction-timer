<template>
    <h1>Reaction Time</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="end" />
    <p v-if="showResult">Reaction time: {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue';
export default {
    name: 'App',
    components: { Block },
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
            this.delay = 2000 + Math.random() * 5000;
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
    margin-top: 60px;
}
</style>
