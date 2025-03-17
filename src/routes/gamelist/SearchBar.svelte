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
    margin-bottom: 1rem;
  }
</style>
