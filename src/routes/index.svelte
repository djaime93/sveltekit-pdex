<script context="module">
    export async function load({page}) {
        const url = `https://pokeapi.co/api/v2/pokemon?limit=150`;
        const res = await fetch(url);
        const data = await res.json();
        const loadedPokemon = data.results.map((data, index) => {
            return {
                name: data.name,
                id: index+1,
                image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${index+1}.png`,
            };
        });
        return {props: {pokemon:loadedPokemon}}
    };
</script>

<script>
    import PokemanCard from "../components/pokemanCard.svelte"
    export let pokemon;
</script>

<h1 class="text-4xl text-center my-8 uppercase">My Sveltekit Pokedex</h1>

<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
    {#each pokemon as pokeman}
    <PokemanCard pokeman={pokeman}/>
    {/each}    
</div>