<template>
	<div class="player">
		<div class="player-name">
			<span class="delete-player">
				<button @click="deletePlayer(name)">X</button>
			</span>
			<h2>{{ name }}</h2>
		</div>
		<!-- Counter Component :) -->
		<Counter id="counter" />
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
#counter {
	margin-right: 1em;
}
.player {
	display: flex;
	align-items: center;
	justify-content: space-between;
	border-top: 1px #7f51fd solid;
}

.player-name {
	display: flex;
	align-items: center;
	margin-left: 2em;
	text-transform: capitalize;
}

.player-name h2 {
	font-weight: 200;
	margin-left: 0.5em;
}

.delete-player {
	margin-right: 0.5em;
}
@media only screen and (max-width: 1000px) {
	#counter {
		margin-right: 0.5em;
	}
	.player-name {
		margin-left: 1em;
	}
}
</style>
