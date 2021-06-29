<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let hero;
  
  function saveHero() {
    dispatch('saveHero',hero)
  }
</script>

<div>
  <div><label for="name">Name</label></div>
  <input type="text" name="name" bind:value={hero.name} />
  <div><label for="birth_year">Birth Year</label></div>
  <input type="text" name="birth_year" bind:value={hero.birth_year} />
  <button on:click={saveHero}>Save</button>
</div>

<h2>The hero is named {hero.name} and they were born in {hero.birth_year}</h2>
