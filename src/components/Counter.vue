<template>
<div id="counter">
    <button @click="decrementScore">-</button>
    {{ score }}
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

    -webkit-box-shadow: inset 0px 2px 23px -4px rgba(255, 255, 255, 0.062);
    -moz-box-shadow: inset 0px 2px 23px -4px rgba(255, 255, 255, 0.144);
    box-shadow: inset 0px 2px 23px -4px rgba(2, 2, 2, 0.527);
}

button {
    padding: 1em;
    border-radius: 2em;
    border: none;
    box-shadow: 0.5em 0.5em 50px #ad8cfc, 1em 1em 50px #f3eeff34;

    background-color: #7f51fd2c;
}
</style>
