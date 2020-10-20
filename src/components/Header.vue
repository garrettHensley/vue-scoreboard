<template>
<div id="header">
    <h1>scoreboard</h1>
    <span>Players: {{ playerCount }}</span>
</div>
</template>

<script>
export default {
    props: {
        playerCount: Number,
    },
};
</script>

<style scoped>
#header {
    display: flex;
    align-items: center;
    justify-content: space-around;
}

#header h1 {
    text-transform: uppercase !important;
}

#header span {
    font-size: 1.5em;
}
</style>
