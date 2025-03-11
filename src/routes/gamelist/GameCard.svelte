<script>
  import GameLikesComponent from "./GameLikesComponent.svelte";
  let { gamename, gametype, gameyear } = $props();
</script>

<div class="games-card">
  <div>
    <h2>{gamename}</h2>
    <p>{gameyear}</p>
    <p>{gametype}</p>
  </div>
  <GameLikesComponent />
</div>

<style>
  .games-card {
    border: 1px blue solid;
    padding: 10px;
    margin: 2px;
    width: 30vw;
  }
</style>
