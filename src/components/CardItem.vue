<template>
	<li class="items">
		<img
			class="pokemons"
			:src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${get_pokemon_id()}.png`"
			alt="${pokemon.name}"
		/>
		<div class="description">
			<span>{{ pokemon.name }}</span>
			<span>#{{ get_pokemon_id() }}</span>
		</div>
	</li>
</template>
<script>
export default {
	props: ["pokemon"],
	mounted() {},
	methods: {
		get_pokemon_id() {
			return Number(this.pokemon.url.split("/")[6]);
		},
	},
};
</script>
