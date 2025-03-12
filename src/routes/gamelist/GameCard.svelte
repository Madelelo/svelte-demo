<script>
  import GameLikesComponent from "./GameLikesComponent.svelte";
  let { gamename, gametype, gameyear } = $props();
</script>

<div class="games-card">
  <div class="games-card-info">
    <h2>{gamename}</h2>
    <p>{gameyear}</p>
    <p>{gametype}</p>
  </div>
  <GameLikesComponent />
</div>

<style>
  .games-card {
    background-color: rgba(167, 167, 255, 0.512);
    border-radius: 5px;
    padding: 10px;
    margin: 2px;
    width: 30vw;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .games-card-info {
    display: flex;
    flex-direction: column;
  }
</style>
