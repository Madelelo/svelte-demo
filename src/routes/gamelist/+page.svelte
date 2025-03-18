<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";
  import LinkButton from "../Components/LinkButton.svelte";
  import SearchBar from "./SearchBar.svelte";

  let games = $state(gamefile.games);
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

<div class="container">
  <h1>Maddes spillbibliotek</h1>
  <SearchBar searchTerm={searchinput} onSearch={searchedList} />
  <LinkButton linkHref="" linkLabel="Tilbake" />

  <div class="game-list">
    {#each games as game}
      <GameCard
        gamename={game.title}
        gameyear={game.year}
        gametype={game.type}
      />
    {/each}
  </div>
</div>

<style>
  .container {
    width: 80%;
    margin: auto;
  }
  .game-list {
    display: flex;
    flex-wrap: wrap;
  }

  :global(body) {
    margin: 0;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  }
</style>
