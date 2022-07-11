<template>
	<h1 class="title">Pokedex</h1>
	<Input></Input>
	<Card></Card>
</template>

<script>
import Input from "../src/components/Input.vue";
import Card from "../src/components/Card.vue";
export default {
	components: {
		Input,
		Card,
	},
};
</script>

<style lang="scss">
@import "@/assets/_shared.scss";

* {
	background-color: $background;
}

.title {
	font-family: "Poppins";
	font-size: 42px;
	font-weight: 200;
	margin: 50px 0 0 50px;
}
</style>
