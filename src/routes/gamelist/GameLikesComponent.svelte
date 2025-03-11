<script>
  let likesCount = 0;

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
</style>
