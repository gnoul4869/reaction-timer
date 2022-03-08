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
        if (this.score < 150) {
            this.rank = 'Inhuman reaction 👀';
            this.color = '#0faf87';
        } else if (this.score < 250) {
            this.rank = "That's fast 😲";
            this.color = 'green';
        } else if (this.score < 350) {
            this.rank = 'Nice reaction time 😉';
            this.color = 'orange';
        } else {
            this.rank = 'Is that your fastest reaction time? 😳';
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
