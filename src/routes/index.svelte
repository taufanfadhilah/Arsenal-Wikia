<script>
  import { onMount } from "svelte";
  import Player from "../components/Player.svelte";
  import axios from "axios";

  let players = [];

  onMount(() => {
    axios
      .get(
        "https://www.thesportsdb.com/api/v1/json/1/searchplayers.php?t=Arsenal"
      )
      .then(res => (players = res.data.player))
      .catch(err => console.log(err));
  });
</script>

<style>
  .main {
    background-color: #9e2321;
    padding-top: 100px;
  }
  .content {
    min-height: 500px;
    background: linear-gradient(180deg, #df332f 0%, #481f1e 80.21%);
    border-radius: 30px 30px 0px 0px;
    padding: 100px 35px;
    display: grid;
    grid-template-columns: repeat(2, auto);
  }
  .loading {
    min-height: 500px;
    background: linear-gradient(180deg, #df332f 0%, #481f1e 80.21%);
    border-radius: 30px 30px 0px 0px;
    padding: 100px 35px;
    text-align: center;
    color: white;
  }
  .img-logo {
    width: 130px;
    height: 152.82px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: -90px;
  }

  @media only screen and (min-width: 768px) {
    .content {
      width: 460px;
      margin-left: auto;
      margin-right: auto;
    }
    .loading {
      width: 460px;
      margin-left: auto;
      margin-right: auto;
    }
  }
</style>

<div class="main">
  <img src="images/arsenal.png" alt="arsenal logo" class="img-logo" />
  {#if players.length < 1}
    <div class="loading">
      <h4>Getting players data</h4>
    </div>
  {:else}
    <div class="content">
      {#each players as player}
        <Player {player} />
      {/each}
    </div>
  {/if}
</div>
