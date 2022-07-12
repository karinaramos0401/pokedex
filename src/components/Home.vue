<template>
	<h1 class="title">Pokedex</h1>
	<Card></Card>
</template>

<script>
import Card from "../components/Card.vue";
export default {
	components: {
		Card,
	},
};
</script>

<style lang="scss">
@import "@/assets/_shared.scss";

* {
	background-color: $background;
}

body {
	padding: 3.125rem;
}

.title {
	font-family: "Poppins";
	font-size: 2.625rem;
	font-weight: 200;
	padding-left: 2.4375rem;
}
</style>
