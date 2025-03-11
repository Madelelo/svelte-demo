<script>
  import GameCard from "../gamelist/GameCard.svelte";
  import gamefile from "../gamelist/games.json";
  import LinkButton from "../LinkButton.svelte";

  let games = gamefile.games;
  console.log(games[0].title);
</script>

<h1>Maddes spillbibliotek</h1>
<LinkButton linkHref="" linkLabel="Tilbake" />

<div>
  {#each games as game}
    <GameCard gamename={game.title} gameyear={game.year} gametype={game.type} />
  {/each}
</div>

<style>
  div {
    display: flex;
    flex-wrap: wrap;
  }
</style>
