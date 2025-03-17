<script>
  let likesCount = $state(0);

  function addLikes() {
    likesCount += 1;
  }
  function removeLikes() {
    likesCount -= 1;
  }
</script>

<div>
  Likes: {likesCount}

  <button onclick={removeLikes}>-</button>
  <button onclick={addLikes}>+</button>
</div>

<style>
  div {
    text-align: right;
  }
  button {
    background-color: rgb(76, 49, 102);
    color: white;
    font-weight: bolder;
    border-radius: 4px;
  }
</style>
