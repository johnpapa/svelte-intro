<script>
  import HeroDetail from './HeroDetail.svelte';
  import HeroesList from './HeroesList.svelte';

  export let name;
  let hero = { name: 'Landon', birth_year: '1917' };
  const heroes = [
    { id: 10, name: 'John', birth_year: '1999' },
    { id: 12, name: 'Colleen', birth_year: '2000' },
    { id: 14, name: 'Oliver', birth_year: '2019' },
  ];
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
  <HeroesList />
  <!-- <HeroesList {heroes} /> -->
  <!-- <HeroDetail {hero} /> -->
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
