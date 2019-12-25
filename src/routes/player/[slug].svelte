<script>
  import { goto } from "@sapper/app";
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
    height: 165px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: -70px;
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
  }
  .description {
    text-align: justify;
    font-size: 14px;
    margin-bottom: 50px;
  }
</style>

<div class="main">
  <img src="images/ozil.png" alt="player image" class="img-logo" />
  <div class="content">
    <p class="bold name">Mesut Ozil</p>
    <div class="row">
      <p class="bold">Nationality</p>
      <p style="text-align: right;">Germarny</p>
    </div>
    <div class="row">
      <p class="bold">Date Born</p>
      <p style="text-align: right;">1988-10-25</p>
    </div>
    <div class="row">
      <p class="bold">Player Number</p>
      <p style="text-align: right;">10</p>
    </div>
    <p class="bold underline">About Me</p>
    <p class="description">
      Mesut Özil (born 15 October 1988) is a German footballer who plays for
      English club Arsenal and the German national team. Özil has been a youth
      national team member since 2006, and a member of the German national team
      since 2009. He gained international attention during the 2010 FIFA World
      Cup and was nominated for the Golden Ball Award, which is awarded to the
      tournament's best player.
    </p>
    <p class="underline" style="font-size: 12px" on:click={goBack}>
      Return back
    </p>
  </div>
</div>
