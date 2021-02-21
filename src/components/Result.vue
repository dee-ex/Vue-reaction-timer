<template>
    <p>Reaction time - {{ score }} (ms)</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: [
        'score',
    ],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'Your reaction is as fast as light'
        } else if (this.score < 400) {
            this.rank = 'Wow, quite quick'
        } else if (this.score < 600) {
            this.rank = 'Not too slow'
        } else {
            this.rank = 'Are you sleepy? Too slow'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
    .warning {
        color: red;
    }
</style>