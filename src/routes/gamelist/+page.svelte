<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";

  let games = gamefile.games;
  console.log(games[0].title);
</script>

<h1>Maddes spillbibliotek</h1>
<div>
  {#each games as game}
    <GameCard gamename={game.title} gameyear={game.year} gametype={game.type} />
  {/each}
</div>

<a class="nav-button" href="/"> ... tilbake </a>

<style>
  div {
    display: flex;
    flex-wrap: wrap;
  }
</style>
