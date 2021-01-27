<script lang="ts">
  import { toTitleCase } from '../utils.js'

  export let name: string
  export let url: string

  const urlArray = url.split('/')
  const indexLocation = urlArray.length - 2

  const index = urlArray[indexLocation]

  const imgurl = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${index}.png`
</script>


<div class="w-72 p-2">
  <div class="bg-white px-6 py-8 rounded-lg shadow-lg text-center">
    <h2 class="font-medium text-gray-700">{toTitleCase(name, '-')}</h2>
    <img 
      class="w-auto mx-auto rounded-xl"
      src={imgurl}
      alt={name}/>
    <button class="px-4 py-2 bg-red-600 text-white rounded">Capture</button>
  </div>
</div>