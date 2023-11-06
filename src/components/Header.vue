<template>
    <header class="container">
        <h1 class="header">
            League {{ heading }}
        </h1>
    </header>
</template>
<script>
export default {
    data() {
        return {
            heading: '',
        }
    },
    mounted() {
        const currentHeading = this.$route.path === '/leaderboard' ? 'Standings' : 'Schedule';

        this.heading = currentHeading;
    }
}
</script>
<style>
.header {
    margin: 60px 0 20px;
    padding: 0;
    text-align: center;
    font-size: 24px;
    color: #182C62;
    font-family: 'Open sans', sans-serif;
}
</style>