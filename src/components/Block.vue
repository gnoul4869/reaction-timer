<template>
    <div class="block" v-if="showBlock" @click="calcResult">Click me</div>
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
            this.reactionTime = performance.now();
            console.log(this.reactionTime);
        }, this.delay);
    },
    methods: {
        calcResult() {
            this.reactionTime = Math.round(performance.now() - this.reactionTime - 16 - 30);
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
