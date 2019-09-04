<template>
  <div class="above-the-fold">
    <h1>Hesehus</h1>
    <router-link class="case-home-button" to="/">
      <HomeButton/>
    </router-link>
    <h2>Motion graphics and React</h2>
    <div class="info-box info-about">
      <h3>About</h3>
      <p>
        Hesehus is the largest e-commerce solution provider
        in Denmark. This project was part of my exam at MMD, and additional
        freelance work after the exam.
      </p>
    </div>
    <div class="info-box info-challange">
      <h3>Challange</h3>
      <p>
        Hesehus had 2 concerns: they needed to display their cases at e-commerce fairs and
        their work process to new clients in a propper way.
        Usually at fairs, cases from their website are shown on a large screen, however those
        contain a lot of text. The cases should be shown in a manner more
        suitable for a fair, while their work process should give an overview for new
        customers.
      </p>
    </div>
    <div class="info-box info-thoughts">
      <h3>Thoughts</h3>
      <p>
        At fairs Hesehus is present among many other brands. To bring attention to their work,
        the cases will be shown with motion graphics videos to grab attention with visuals and movement.
        The videos should be an appetizer of Hesehus’ work. At the fair users can control the videos with
        an interface.
      </p>
    </div>
  </div>
</template>
<style lang="scss">
$transition: all 0.1s ease-in;
.above-the-fold {
  display: grid;
  grid-template-rows: repeat(18, 4.94vh);
  grid-row-gap: 1vh;
  grid-template-columns: repeat(24, 3.125vw);
  grid-column-gap: 1vw;
  margin: 2vh 1vw;
  .case-home-button {
    grid-column-start: 24;
    grid-row-start: 1;
    justify-self: end;
    align-self: start;
    transform: translate(-26px, 8px);
  }
  h1 {
    grid-column-start: 2;
    grid-column-end: 8;
    grid-row-start: 1;
    font-size: 242px;
    font-family: "Poppins", sans-serif;
    color: black;
    margin-left: -0.067em;
  }

  h2 {
    grid-column-start: 2;
    grid-column-end: 5;
    grid-row-start: 8;
    align-self: end;
    font-family: "Source Code Pro", monospace;
    font-size: 28px;
    font-weight: 400;
  }

  .info-box {
    grid-row-start: 11;
    display: grid;
    grid-template-columns: repeat(8, 3.125vw);
    grid-column-gap: 1vw;
    h3 {
      grid-column-start: 1;
      grid-column-end: 1;
      writing-mode: vertical-lr;
      justify-self: end;
      font-family: "Poppins", sans-serif;
      font-size: 21px;
    }
    p {
      grid-column-start: 2;
      grid-column-end: 8;
      font-family: "Source Code Pro", monospace;
    }
  }
  .info-about {
    grid-column-start: 1;
    grid-column-end: 9;
  }
  .info-challange {
    grid-column-start: 9;
    grid-column-end: 17;
  }
  .info-thoughts {
    grid-column-start: 17;
    grid-column-end: 25;
  }
}
@keyframes rumble{
    0%{
      transform: translate3D(0px, 0px,0);
    }
    10%{
      transform: translate3D(1px, 0.5px,0);
    }
    40%{
      transform: translate3D(0px, 0px,0);
    }
    60%{
      transform: translate3D(-1px, 1px,0);
    }
    80%{
      transform: translate3D(0px, 0.5px,0);
    }
    100%{
      transform: translate3D(1px, 0px,0);
    }
  }

</style>
<script>
import HomeButton from "@/components/HomeButton.vue";
export default {
  name: "CasesAboveThefold",
  components: {
    HomeButton
  }
};
</script>
