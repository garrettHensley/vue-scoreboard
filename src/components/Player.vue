<template>
	<div class="player">
		<div class="player-name">
			<span class="delete-player">
				<button @click="deletePlayer(name)">x</button>
				<template v-if="editing" style="margin-left: 1.5em;"
					><input
						type="text"
						v-model="newName"
						:placeholder="name"
						maxlength="10"
					/>
					<button
						id="confirm-edit"
						@click="
							editName();
							editing = !editing;
						"
						:disabled="newName.length <= 0"
					>
						✓
					</button></template
				>
			</span>

			<h2>
				<span @click="editing = !editing" v-if="!editing">{{ trueName }}</span>
			</h2>
		</div>
		<!-- Counter Component :) -->
		<Counter id="counter" v-if="!editing" />
	</div>
</template>

<script>
import Counter from "./Counter";

export default {
	components: {
		Counter,
	},
	data() {
		return {
			editing: undefined,
			newName: "",
			trueName: undefined,
		};
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
	mounted() {
		this.trueName = this.name;
	},
	methods: {
		deletePlayer(playerName) {
			this.$emit("delete-player", playerName); // pass up player name to be deleted
		},
		editName() {
			let temp = {
				newName: this.newName,
				oldName: this.name,
			};
			this.$emit("edit-player", temp);
			this.trueName = this.newName;
			this.newName = "";
		},
	},
};
</script>

<style scoped>
a {
	text-decoration: none;
	color: black;
}

.delete-player {
	margin-left: 0 !important;
}

#counter {
	margin-right: 1em;
}

#confirm-edit {
	border-radius: 0 0.5em 0.5em 0;
	margin-left: 0;
	height: 2.15em;
}

.player {
	display: flex;
	align-items: center;
	justify-content: space-between;
	border-top: 1px #7f51fd solid;
	height: 4.5em;
}

.player-name {
	display: flex;
	align-items: center;
	margin-left: 2em;
	text-transform: capitalize;
}

.player-name h2 {
	font-weight: 200;
	margin-left: 1em;
}

.input-container {
	align-items: center;
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
