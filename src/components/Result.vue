<template>
    <p>Reaction time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        };
    },
    mounted() {
        if (this.score < 100) {
            this.rank = 'Inhuman reaction 👀';
        } else if (this.score < 200) {
            this.rank = "That's fast 😲";
        } else if (this.score < 400) {
            this.rank = 'Nice reaction 😉';
        } else {
            this.rank = 'Is that your fastest reaction? 😳';
        }
    },
};
</script>

<style>
.rank {
    font-size: 1.4rem;
    color: #0faf87;
    font-weight: bold;
}
</style>
