<script>
  let { gamename, gametype, gameyear } = $props();

  //TODO add likes button with state
</script>

<div>
  <h2>{gamename}</h2>
  <p>{gameyear}</p>
  <p>{gametype}</p>
</div>

<style>
  div {
    border: 1px blue solid;
    padding: 10px;
    margin: 2px;
    width: 30vw;
  }
</style>
