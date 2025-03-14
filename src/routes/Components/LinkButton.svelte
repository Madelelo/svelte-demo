<script>
  let { linkLabel, linkHref } = $props();
</script>

<a href="/{linkHref}"> <div class="nav-button">{linkLabel}</div></a>

<style>
  :global(.nav-button) {
    background-color: rgb(167, 167, 255);
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    color: aliceblue;
    font-size: small;
    border-radius: 4px;
    height: 20px;
    width: 20%;
    text-align: center;
    padding: 5px;
    margin: 2px;
  }
</style>
