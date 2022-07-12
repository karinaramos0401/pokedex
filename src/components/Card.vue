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
				console.log("banana", this.search);
			});
		},
	},
};
</script>
<style lang="scss">
@import "@/assets/_shared.scss";

.pokemons {
	background-color: #ffff;
	padding-left: 0px !important;
}

.search {
	margin: 50px 0 20px 39px;
	border-radius: 10px;
	height: 40px;
	width: 34.375rem;
	border: 2px;
	outline: 0;
	border: 1px solid #696969;
	padding-left: 10px;
	background-color: #ffff;
}

.container {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
	gap: 5px 14px;
}

.items {
	margin-top: 10px;
	background-color: #ffff;
	height: 138px;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
	padding: 15px;
}

.description {
	display: flex;
	justify-content: space-between;
	width: 100%;
	background-color: #ffff;
}

.description > span {
	font-size: 18px;
	background-color: #ffff;
}
</style>
