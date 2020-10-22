<template>
	<div id="counter">
		<button @click="decrementScore">-</button>
		<div>{{ score }}</div>
		<button @click="incrementScore">+</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			score: 0,
		};
	},
	methods: {
		incrementScore() {
			this.score++;
		},
		decrementScore() {
			this.score--;
		},
	},
};
</script>

<style lang="scss" scoped>
#counter {
	width: 20%;
	border: 1px rgba(0, 0, 0, 0.048) solid;
	padding: 0.5em;
	font-size: 1.5em;
	display: flex;
	justify-content: space-between;

	-webkit-box-shadow: inset 0px 2px 2px -4px rgba(255, 255, 255, 0.062);
	-moz-box-shadow: inset 0px 2px 2px -4px rgba(255, 255, 255, 0.144);
	box-shadow: inset 0px 2px 2px -1px rgba(131, 127, 127, 0.308);
}
@media only screen and (max-width: 1000px) {
	#counter {
		width: 30%;
	}
}
</style>
