<template>
    <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return { showBlock: false, timer: null, reactionTime: 0 };
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('end', this.reactionTime);
        },
    },
};
</script>

<style>
.block {
    width: 70vw;
    max-width: 20rem;
    border-radius: 1.25rem;
    background: #0faf87;
    color: white;
    text-align: center;
    font-size: 1.6rem;
    padding: 5rem 0;
    margin: 2.5rem auto;
    cursor: pointer;
}
</style>
