<script>
  import HeroDetail from './HeroDetail.svelte';

  // export let heroes;

  let selectedHero;

  let heroesPromise = getHeroes();

  async function getHeroes() {
    const response = await fetch('https://swapi.dev/api/people');
    const json = await response.json();
    return json.results;
  }

  function save({ detail: heroToSave }) {
    console.table(heroToSave);
  }
</script>

<h1>Heroes List</h1>
{#await heroesPromise}
  Heroes are in a galaxy far far away
{:then heroes}
  <!-- heroesPromise was fulfilled -->
  <ul>
    {#each heroes as hero}
      <li class="row" on:click={() => (selectedHero = hero)} class:selected={selectedHero === hero}>{hero.name}</li>
    {/each}
  </ul>
{:catch error}
  <!-- heroesPromise was rejected -->
  <div class="error">
    <p>The Sith have wiped out the heroes</p>
    <p>{error}</p>
  </div>
{/await}

<!-- <ul>
  {#each heroes as hero}
    <li class="row" on:click={() => (selectedHero = hero)} class:selected={selectedHero === hero}>{hero.name}</li>
  {/each}
</ul> -->

{#if selectedHero}
  <HeroDetail hero={selectedHero} on:saveHero={save} />
{/if}

<style>
  ul {
    list-style-type: none;
    padding: 4px;
  }
  ul > li {
    padding: 4px;
    cursor: pointer;
  }
  .selected {
    background-color: yellow;
  }
  .row {
    margin: 10px;
    box-shadow: 0 0 5px gray;
    padding: 10px 20px;
  }
  .error {
    background: rgb(255, 219, 219);
    padding: 10px 20px;
  }
</style>
