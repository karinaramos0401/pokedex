<template>
	<input class="search" v-model="search" placeholder="Search" />
	<ul class="container">
		<li class="items" v-for="pokemon in filter_pokemons" :key="pokemon.name">
			<img
				class="pokemons"
				:src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${get_pokemon_id(
					pokemon
				)}.png`"
				alt="pokemon.name"
			/>
			<div class="description">
				<span>{{ pokemon.name }}</span>
				<span>#{{ get_pokemon_id(pokemon) }}</span>
			</div>
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
		search: "",
	}),
	mounted() {
		axios
			.get("https://pokeapi.co/api/v2/pokemon?limit=151")
			.then((response) => {
				console.log(response);
				this.pokemons = response.data.results;
			});
	},
	methods: {
		get_pokemon_id(pokemon) {
			return Number(pokemon.url.split("/")[6]);
		},
	},
	computed: {
		filter_pokemons() {
			return this.pokemons.filter((item) => {
				return item.name.includes(this.search);
			});
		},
	},
};
</script>
<style lang="scss">
@import "@/assets/_shared.scss";

.pokemons {
	background-color: $white;
	padding-left: 0px !important;
}

.search {
	margin: 3.125rem 0 1.25rem 2.4375rem;
	border-radius: 0.625rem;
	height: 2.5rem;
	width: 34.375rem;
	border: 0.125rem;
	outline: 0;
	border: 1px solid $border;
	padding-left: 0.625rem;
	background-color: $white;
}

.container {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
	gap: 0.3125rem 0.875rem;
}

.items {
	margin-top: 0.625rem;
	background-color: $white;
	height: 8.625rem;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
	padding: 0.9375rem;
}

.description {
	display: flex;
	justify-content: space-between;
	width: 100%;
	background-color: $white;
}

.description > span {
	font-size: 1.125rem;
	background-color: $white;
}
</style>
