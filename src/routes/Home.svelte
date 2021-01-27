<script lang="ts">
  import ky from 'ky'

  import PokemonCard from '../components/PokemonCard.svelte'
  import Input from '../components/Input.svelte'

  let pokemons = []
  let offset = 0
  let amountToLoad = 18 

  interface Data {
    results: []
  }

  $: {
    getPokemon(offset, amountToLoad)
  }

  async function getPokemon(off: number, amt: number) {
    let url = `https://pokeapi.co/api/v2/pokemon?offset=${off}&limit=${amt}`
    const data: Data = await ky.get(url).json()

    pokemons = [...pokemons, ...data.results]
    // console.log(pokemons)
  }

  function handleMoreClick() {
    offset += amountToLoad
  }

</script>

<main class="flex h-screen">
  <div class="flex flex-col mx-auto items-center mt-4 container">

    <div class="max-w-md mb-3">
      <h1 class="font-sans font-bold mb-3 text-3xl">Search for a pokemon</h1>
      <Input />
    </div>

    <div id="container" class="m-auto h-full">
      <div class="flex flex-col sm:flex-row grid grid-cols-6">
        {#each pokemons as { name, url } (url)}
          <PokemonCard {name} {url} />
        {/each}
      </div>
      <div class="text-center">
        <div class="p-3">
          {#if pokemons.length > 0}
            <button
              class="font-sans font-bold bg-red-700 text-white px-4 py-2 rounded"
              type="button"
              id="more-button"
              on:click={handleMoreClick}
            >
              Load More
            </button>
          {/if}
        </div>
      </div>
    </div>

  </div>
</main>
