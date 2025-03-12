<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";
  import LinkButton from "../Components/LinkButton.svelte";
  import Sanityconnector from "./Sanityconnector.svelte";
  let games = gamefile.games;

  let PROJECT_ID = "x9czv3a6";
  let DATASET = "production";
  let QUERY = encodeURIComponent('*[_type == "games"]');
  //let SANITYURL = `https://${PROJECT_ID}.api.sanity.io/v2021-10-21/data/query/${DATASET}?query=${QUERY}`;

  const fetchData = (async () => {
    const response = await fetch(SANITYURL);
    return await response.json();
  })();
</script>

<h1>Maddes spillbibliotek</h1>
<LinkButton linkHref="" linkLabel="Tilbake" />

<div>
  {#await fetchData}
    <p>Loading games...</p>
  {:then data}
    {#each data.result as game}
      <GameCard gamename={game.name} gameyear={game.year} gametype={""} />
    {/each}
  {:catch error}
    <div>
      {#each games as game}
        <GameCard
          gamename={game.title}
          gameyear={game.year}
          gametype={game.type}
        />
      {/each}
    </div>
  {/await}
</div>

<style>
  div {
    display: flex;
    flex-wrap: wrap;
  }
</style>
