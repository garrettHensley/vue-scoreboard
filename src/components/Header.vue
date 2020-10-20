<template>
	<div id="header">
		<div class="title">
			<div class="title-buttons">
				<!-- Add Player Button -->
				<button @click="addingNewPlayer = !addingNewPlayer">
					<template v-if="addingNewPlayer"> - </template>
					<template v-else> + </template>
				</button>
			</div>
			<h1>scoreboard</h1>
		</div>
		<span class="player-count">Players: {{ playerCount }}</span>
	</div>
	<div id="new-player" v-if="addingNewPlayer">
		<button @click="addPlayer">+</button>
		<input
			type="text"
			placeholder="Player Name"
			v-model="name"
			maxlength="10"
		/>
	</div>
</template>

<script>
export default {
	data() {
		return {
			addingNewPlayer: false,
			name: "",
		};
	},
	props: {
		playerCount: Number,
	},
	methods: {
		addPlayer() {
			if (this.name) {
				this.$emit("add-player", this.name);
				console.log(`Added Player "${this.name}"`);
			} else {
				console.log("Name Entry is Invalid!");
				console.log(this.name);
			}
		},
	},
};
</script>

<style scoped>
#header {
	display: flex;
	align-items: center;
	justify-content: space-between;
}

h1 {
	text-transform: uppercase !important;
}

.title {
	display: flex;
	align-items: center;
	margin-left: 2em;
}
.title-buttons {
	display: flex;
	margin-right: 1em;
}

.player-count {
	font-size: 1.5em;
	margin-right: 2em;
}
#new-player {
	margin-left: 2em;
	padding-bottom: 1em;
}
button {
	border-radius: 1.5em;
	height: 2em;
	width: 2em;
	border: none;
}
input {
	border: none;
	border-radius: 0.2em;
	margin-left: 1.5em;
	width: 25em;
	height: 2em;
}

@media only screen and (max-width: 1000px) {
	#new-player {
		margin-left: 1em;
	}
	h1 {
		font-size: 1.5em;
		font-weight: 100;
	}
	.title {
		margin-left: 1em;
	}
	.player-count {
		font-size: 1.2em;
		margin-right: 1em;
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
