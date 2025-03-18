<script>
  let { searchinput, onSearch } = $props();

  function handleInput(event) {
    onSearch(event.target.value);
  }
</script>

<div>
  Find a game:
  <input bind:value={searchinput} on:input={handleInput} />
</div>

<style>
  div {
    border: 1px solid rgb(82, 82, 201);
    border-radius: 5px;
    padding: 10px;
    margin: 2px;
    width: 30vw;
  }
</style>
