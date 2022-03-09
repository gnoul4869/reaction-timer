<template>
    <div class="block" @click="calcResult" :style="{ 'background-color': color }">{{ text }}</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            text: null,
            color: null,
            isCatching: false,
            reactionTime: 0,
            delayTimer: null,
            isFresh: false,
        };
    },
    mounted() {
        this.start();
    },
    methods: {
        start() {
            this.text = 'Wait for it...';
            this.color = 'indianRed';
            this.delayTimer = setTimeout(() => {
                this.text = 'Click now!';
                this.color = '#0faf87';
                this.isCatching = true;
                this.reactionTime = performance.now();
            }, this.delay);
        },
        calcResult() {
            if (this.isCatching) {
                const result = Math.round(performance.now() - this.reactionTime);
                const estimatedResult = result - 16 - 30;
                this.reactionTime = estimatedResult < 1 ? result : estimatedResult;
                this.$emit('end', this.reactionTime);
            } else {
                clearTimeout(this.delayTimer);
                this.text = 'Too soon!';
                this.color = 'steelblue';
                this.$emit('end', 0);
            }
        },
    },
    watch: {
        delay: function (newValue, oldValue) {
            this.start();
        },
    },
};
</script>

<style>
.block {
    width: 70vw;
    max-width: 20rem;
    border-radius: 1.25rem;
    color: white;
    text-align: center;
    font-size: 1.6rem;
    padding: 5rem 0;
    margin: 2.5rem auto;
    cursor: pointer;
}
</style>
