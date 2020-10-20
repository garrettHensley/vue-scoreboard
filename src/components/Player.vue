<template>
<div class="player">
    <div class="player-name">
        <span class="delete-player">
            <button @click="deletePlayer(name)">X</button>
        </span>
        <h2>{{ name }}</h2>
    </div>
    <!-- Counter Component :) -->
    <Counter />
</div>
</template>

<script>
import Counter from "./Counter";

export default {
    components: {
        Counter,
    },
    props: {
        name: {
            type: String,
            default: "Player",
        },
        score: {
            type: Number,
            default: 0,
        },
    },
    methods: {
        deletePlayer(playerName) {
            this.$emit("delete-player", playerName); // pass up player name to be deleted
        },
    },
};
</script>

<style scoped>
.player {
    padding: 0 1em;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top: 1px #7f51fd solid;
}

.player-name {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.player-name h2 {
    font-weight: 200;
}

.delete-player {
    margin-right: 0.5em;
}

button {
    color: #cca4fd;
    font-weight: bolder;
    padding: 1em;
    border-radius: 2em;
    border: none;
    box-shadow: 0.5em 0.5em 50px #ad8cfc, 1em 1em 50px #f3eeff34;

    background-color: #7f51fd2c;
}
</style>
