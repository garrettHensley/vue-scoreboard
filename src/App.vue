<template>
<div class="container">
    <Header :playerCount="players.length" />
    <div>
        <!-- Players go here -->
        <Player v-for="player in players" :key="player.id" :name="player.name" @delete-player="deletePlayer" />
    </div>
</div>
</template>

<script>
import Header from "./components/Header.vue";
import Player from "./components/Player.vue";
export default {
    name: "App",
    components: {
        Header,
        Player,
    },
    data() {
        return {
            players: [{
                    name: "Gare",
                    id: 1,
                },
                {
                    name: "Michael",
                    id: 2,
                },
                {
                    name: "Stephanie",
                    id: 3,
                },
                {
                    name: "Soren",
                    id: 4,
                },
            ],
        };
    },
    methods: {
        deletePlayer(e) {
            console.log(`Deleting player "${e}"`);
            this.players = this.players.filter((player) => {
                return player.name !== e;
            });
        },
    },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap");

html body {
    font-family: "Quicksand", sans-serif;

    background: linear-gradient(328deg,
            rgba(180, 218, 252, 1) 0%,
            rgba(204, 164, 253, 1) 100%);
    background-repeat: no-repeat;
    background-attachment: fixed;
}

.container {
    margin: 0 auto;
    width: 50%;
    border: 1px #7f51fd solid;
    border-radius: 0.5em;

    background: #bbbbf9;
    -webkit-box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
    -moz-box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
    box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
}
</style>
