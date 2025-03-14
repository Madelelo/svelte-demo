<script>
  let searchinput = $state("Search...");
</script>

<input bind:value={searchinput} />

<h1>{searchinput}!</h1>

<input bind:value={() => searchinput, (v) => (searchinput = v.toLowerCase())} />
