<template>
    <h2>
        Reaction time: <span :style="{ color: color }">{{ score }}</span> ms
    </h2>
    <p class="rank" :style="{ color: color }">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
            color: null,
        };
    },
    mounted() {
        if (this.score < 100) {
            this.rank = 'Inhuman reaction 👀';
            this.color = '#0faf87';
        } else if (this.score < 200) {
            this.rank = "That's fast 😲";
            this.color = 'green';
        } else if (this.score < 400) {
            this.rank = 'Nice reaction 😉';
            this.color = 'orange';
        } else {
            this.rank = 'Is that your fastest reaction? 😳';
            this.color = 'red';
        }
    },
};
</script>

<style>
.rank {
    font-size: 2.5rem;
    font-weight: bold;
}
</style>
