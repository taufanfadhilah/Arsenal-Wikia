<script>
  import Player from "../components/Player.svelte";
</script>

<style>
  .main {
    background-color: #9e2321;
    padding-top: 100px;
  }
  .content {
    background: linear-gradient(180deg, #df332f 0%, #481f1e 80.21%);
    border-radius: 30px 30px 0px 0px;
    padding: 100px 35px;
    display: grid;
    grid-template-columns: repeat(2, auto);
  }
  .img-logo {
    width: 130px;
    height: 152.82px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: -90px;
  }
</style>

<div class="main">
  <img src="images/arsenal.png" alt="arsenal logo" class="img-logo" />
  <div class="content">
    {#each [1, 2, 3, 4, 5, 6, 7] as player}
      <Player />
    {/each}
  </div>
</div>
