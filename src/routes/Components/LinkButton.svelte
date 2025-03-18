<script>
  let { linkLabel, linkHref } = $props();
</script>

<a href="/{linkHref}"> <div class="nav-button">{linkLabel}</div></a>

<style>
  :global(.nav-button) {
    background-color: rgb(76, 49, 102);

    color: azure;
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    font-size: small;
    border-radius: 4px;
    height: 20px;
    width: 30vw;
    text-align: center;
    padding: 5px;
    margin: 2px;
  }
</style>
