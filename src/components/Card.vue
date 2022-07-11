<template>
	<ul class="container">
		<li v-for="pokemon in pokemons" :key="pokemon.name" class="items">
			<img
				class="img"
				:src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${get_pokemon_id(
					pokemon
				)}.png`"
				alt="pokemon.name"
			/>
			<span class="description">{{ pokemon.name }}</span>
			<span class="description">#{{ get_pokemon_id(pokemon) }}</span>
		</li>
	</ul>
</template>

<script>
import axios from "axios";
export default {
	name: "App",
	components: {},
	data: () => ({
		pokemons: [],
	}),
	mounted() {
		axios
			.get("https://pokeapi.co/api/v2/pokemon?limit=151")
			.then((response) => {
				this.pokemons = response.data.results;
			});
	},
	methods: {
		get_pokemon_id(pokemon) {
			return Number(pokemon.url.split("/")[6]);
		},
	},
};
</script>
<style lang="scss">
@import "@/assets/_shared.scss";

img {
	width: 150px;
	background-color: #ffff;
}

.container {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
	gap: 5px 14px;
}

.items {
	padding-left: 50px;
	margin-top: 10px;
	overflow: hidden;
	background-color: #ffff;
	margin-left: 50px;
}

.description {
	font-size: 18px;
	text-align: justify;
	background-color: #ffff;
}
</style>
