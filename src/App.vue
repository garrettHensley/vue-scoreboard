<template>
	<div id="app" class="container">
		<Header :playerCount="players.length" @add-player="addPlayer" />
		<div>
			<!-- Players go here -->
			<Player
				v-for="player in players"
				:key="player.id"
				:name="player.name"
				@delete-player="deletePlayer"
				@edit-player="editPlayer"
			/>
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
			players: [
				{
					name: "Gare",
					score: 0,
				},
				{
					name: "Michael",
					score: 0,
				},
				{
					name: "Stephanie",
					score: 0,
				},
				{
					name: "Chris",
					score: 0,
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
		editPlayer(temp) {
			for (let i = 0; i < this.players.length; i++) {
				if (this.players[i].name == temp.oldName) {
					this.players[i].name = temp.newName;
					break;
				}
			}
			console.log(this.players);
		},
		addPlayer(name) {
			this.players.push({
				name: name,
			});
			console.log(this.players[0].id);
		},
	},
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap");

html body {
	font-family: "Quicksand", sans-serif;

	background: linear-gradient(
		328deg,
		rgba(180, 218, 252, 1) 0%,
		rgba(204, 164, 253, 1) 100%
	);
	background-repeat: no-repeat;
	background-attachment: fixed;
}

.container {
	margin: 0 auto;
	width: 60%;
	border: 1px #cfc0f8 solid;
	border-radius: 0.5em;

	background: #bbbbf9;
	-webkit-box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
	-moz-box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
	box-shadow: 0px 2px 15px 0.3em rgba(0, 0, 0, 0.5);
}
button {
	color: #fa02e5;
	font-weight: bolder;
	height: 2em;
	width: 2em;

	border-radius: 2em;
	border: 1px solid #f202fa2d;
	box-shadow: 0.05em 0.1em 1em #4f44686b, inset 0.05em 0.1em 20px #f7f7f7a6;

	background-color: #7f51fd2c;
}

input {
	border: none;
	border-radius: 0.2em;
	width: 25em;
	height: 2em;
	margin-left: 1.5em;
}

@media only screen and (max-width: 1000px) {
	.container {
		width: 100%;
	}
	input {
		border: none;
		border-radius: 0.2em;
		margin-left: 1.5em;
		width: 10em;
		height: 2em;
	}
}
</style>
