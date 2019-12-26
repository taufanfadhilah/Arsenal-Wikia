<script context="module">
  export async function preload(page, session) {
    const { name } = page.params;
    const res = await this.fetch(
      `https://www.thesportsdb.com/api/v1/json/1/searchplayers.php?p=${name}`
    );
    let player = await res.json();
    player = player.player[0];
    return { player };
  }
</script>

<script>
  import { goto } from "@sapper/app";

  export let player;

  const goBack = () => {
    goto("/");
  };
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
  }
  .row {
    display: grid;
    grid-template-columns: repeat(2, auto);
  }
  .img-logo {
    width: 140px;
    height: 140px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: -70px;
    border-radius: 10px;
  }
  p {
    color: white;
    font-size: 20px;
    line-height: 20px;
  }
  .name {
    font-size: 26px !important;
    text-align: center;
  }
  .bold {
    font-weight: bold;
    font-size: 20px;
  }
  .underline {
    text-decoration-line: underline;
    cursor: pointer;
  }
  .description {
    text-align: justify;
    font-size: 14px;
    margin-bottom: 50px;
  }
  .fade-in {
    opacity: 1;
    animation-name: fadeInOpacity;
    animation-iteration-count: 1;
    animation-timing-function: ease-in;
    animation-duration: 1s;
  }

  @keyframes fadeInOpacity {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  @media only screen and (min-width: 768px) {
    .content {
      width: 460px;
      margin-left: auto;
      margin-right: auto;
    }
  }
</style>

<div class="main">
  <img src={player.strThumb} alt="player image" class="img-logo fade-in" />
  <div class="content">
    <p class="bold name">{player.strPlayer}</p>
    <div class="row">
      <p class="bold">Nationality</p>
      <p style="text-align: right;">{player.strNationality}</p>
    </div>
    <div class="row">
      <p class="bold">Date Born</p>
      <p style="text-align: right;">{player.dateBorn}</p>
    </div>
    <div class="row">
      <p class="bold">Player Number</p>
      <p style="text-align: right;">{player.strNumber || '-'}</p>
    </div>
    <p class="bold underline">About Me</p>
    <p class="description">{player.strDescriptionEN}</p>
    <p class="underline" style="font-size: 12px" on:click={goBack}>
      Return back
    </p>
  </div>
</div>
