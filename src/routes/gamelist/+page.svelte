<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";
  import LinkButton from "../Components/LinkButton.svelte";
  import SearchBar from "./SearchBar.svelte";

  let games = $state(gamefile.games);

  //SEARCH bar
  let searchinput = $state("Search...");

  function searchedList(searchterm) {
    let originalGameList = games;
    if (searchterm == "") {
      games = gamefile.games;
    } else
      games = games.filter((game) => {
        return game.title.includes(searchterm) == true;
      });
  }
</script>

<h1>Maddes spillbibliotek</h1>

<div>
  Find a game:
  <input
    bind:value={() => searchinput, (v) => ((searchinput = v), searchedList(v))}
  />
</div>

<div>
  {#each games as game}
    <GameCard gamename={game.title} gameyear={game.year} gametype={game.type} />
  {/each}
</div>

<LinkButton linkHref="" linkLabel="Tilbake" />

<style>
  div {
    display: flex;
    flex-wrap: wrap;
  }
  :global(body) {
    margin: 0;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  }
</style>
