<script>
    // import Loading from './Loading.svelte'
    
    export let loading
    const handleInput = (event) =>
        pokename = event.target.value
    
    </script>
    
    {#if loading}
        <!-- <Loading/> -->
        {:else}
        <input class="shadow-xl bg-white h-10 px-5 pr-10 rounded text-sm" placeholder="Pokemon">
        <button class="inline-flex py-2 px-4 bg-red-600 text-white font-semibold rounded-lg shadow-md transform transition motion-reduce:transform-none hover:scale-110 duration-500 focus:outline-none"> 🔍 </button>
    {/if}
<scrip/>