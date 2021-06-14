<script context="module">
    export async function load({page}) {
        const url = `https://pokeapi.co/api/v2/pokemon?limit=150`;
        const res = await fetch(url);
        const data = await res.json();
        const loadedPokemon = data.results.map((data, index) => {
            return {
                name: data.name,
                id: data.id,
                image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${index+1}.png`,
            };
        });
        return {props: {pokemon:loadedPokemon}}
    };
</script>

<script>
    export let pokemon;
    console.log(pokemon)
</script>

<h1>My Sveltekit Pokedex</h1>

{#each pokemon as pokeman}
<p>{pokeman.name}</p>
{/each}
