<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";
  import LinkButton from "../Components/LinkButton.svelte";
  import SearchBar from "./SearchBar.svelte";
  let games = $state(gamefile.games);

  //GET data from sanity
  let PROJECT_ID = "x9czv3a6";
  let DATASET = "production";
  let QUERY = encodeURIComponent('*[_type == "games"]');
  //let SANITYURL = `https://${PROJECT_ID}.api.sanity.io/v2021-10-21/data/query/${DATASET}?query=${QUERY}`;

  const fetchData = (async () => {
    const response = await fetch(SANITYURL);
    return await response.json();
  })();

  //SEARCH bar
  let searchinput = $state("Search...");

  function searchedList(searchterm) {
    let originalGameList = games;
    if (searchterm == "") {
      games = gamefile.games;
    } else
      games = games.filter((game) => {
        console.log(game.title.startsWith(searchterm));
        return game.title.includes(searchterm) == true;
      });
  }
</script>

<h1>Maddes spillbibliotek</h1>
<LinkButton linkHref="" linkLabel="Tilbake" />

<div>
  Find a game:
  <input
    bind:value={() => searchinput, (v) => ((searchinput = v), searchedList(v))}
  />
</div>

<div>
  {#await fetchData}
    <p>Loading games...</p>
  {:then data}
    <div>
      <GameList gamelist={data} />
    </div>
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
