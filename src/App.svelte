<script lang="ts">
  import { Router, Link, Route } from 'svelte-routing'
  import Home from './routes/Home.svelte'

  export let url = ''
</script>

<Router {url}>
  <main class="py-4">
    <Route path="/" component={Home} />
  </main>
</Router>

<style global>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>