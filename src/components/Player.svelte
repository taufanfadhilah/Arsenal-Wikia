<script>
  import { goto } from "@sapper/app";
  import { css } from "emotion";

  export let player;

  export const stylePlayer = css`
    width: 110px;
    height: 130px;
    background: linear-gradient(
        180deg,
        rgba(0, 0, 0, 0) 0%,
        rgba(0, 0, 0, 0.375) 51.56%,
        #000000 100%
      ),
      url(${player.strThumb});
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 10px;
    margin-top: 15px;
    margin-bottom: 15px;
    margin-left: auto;
    margin-right: auto;
    cursor: pointer;
  `;

  const onClick = () => {
    goto(`player/${player.strPlayer}`);
  };
</script>

<style>
  .player-name {
    font-size: 12px;
    color: white;
    width: 86px;
    margin: 100px 15px 0px 15px;
    text-align: center;
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
</style>

<div class="{stylePlayer} fade-in" on:click={onClick}>
  <p class="player-name">{player.strPlayer}</p>
</div>
