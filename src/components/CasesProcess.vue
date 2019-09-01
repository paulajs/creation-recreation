<template>
  <div class="case-process">
    <div class="process-inspiration">
      <div class="case-section-header header-inspiration">
        <h5>Inspiration</h5>
      </div>
      <p
        class="inspiration-text"
      >Moodboard of Hesehus’ visual identity and research of e-commerce fairs.</p>
      <img class="hesehus-indtryk" src="../assets/img/hesehus-indtryk.jpg" alt />
      <img class="hesehus-messe" src="../assets/img/hesehus-messe.jpg" alt />
      <div class="case-section-header header-experimentation">
        <h5>Experimentation</h5>
      </div>
      <p class="experimentation-text">
        Work process/ customer journey represented by boat and by spaceship, and
        development of graphic universe for the cases.
      </p>
      <img class="hesehus-boat" src="../assets/img/hesehus-boat.png" alt />
      <img class="hesehus-space" src="../assets/img/hesehus-space.png" alt />
      <img class="hesehus-ideation" src="../assets/img/hesehus-ideation.jpg" alt />
      <div class="case-section-header header-storyboards">
        <h5>Storyboards</h5>
      </div>
      <p class="storyboards-text">Example of a storyboard for the case Inspiration.</p>
      <img
        class="hesehus-storyboard-inspiration"
        src="../assets/img/hesehus-storyboard-inspiration.png"
        alt
      />
      <img
        class="hesehus-storyboard-fristads-kansas"
        src="../assets/img/hesehus-storyboard-danoffice.png"
        alt
      />
    </div>
  </div>
</template>
<style lang="scss">
.case-process {
  .process-inspiration {
    grid-row-start: 3;
    font-family: "Source Code Pro", monospace;
    display: grid;
    grid-template-rows: repeat(90, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    margin: 0 1vw;
    .case-section-header {
      color: white;
      background: black;
      grid-column-start: 1;
      grid-column-end: 6;
      display: grid;
      grid-template-columns: repeat(24, 3.125vw);
      grid-column-gap: 1vw;
      height: 3.06vh;
      transform: translateX(-1vw);
      h5 {
        grid-column-start: 2;
        align-self: center;
        font-size: 18px;
        transform: translateX(1vw);
        font-weight: 300;
      }
    }
    .header-inspiration {
      grid-row-start: 2;
    }
    .header-experimentation {
      grid-row-start: 19;
    }
    .header-storyboards {
      grid-row-start: 64;
    }
    .inspiration-text {
      grid-row-start: 3;
    }
    .experimentation-text {
      grid-row-start: 20;
    }
    .storyboards-text {
      grid-row-start: 65;
    }
    p {
      grid-column-start: 2;
      grid-column-end: 6;
    }
    .hesehus-indtryk {
      grid-row-start: 5;
      grid-column-start: 2;
    }
    .hesehus-messe {
      grid-row-start: 5;
      grid-column-start: 14;
      height: 635px;
    }
    .hesehus-boat {
      grid-row-start: 23;
      grid-column-start: 4;
      height: 91vh;
    }
    .hesehus-space {
      grid-row-start: 23;
      grid-column-start: 14;
      height: 91vh;
    }
    .hesehus-ideation {
      grid-row-start: 43;
      grid-column-start: 3;
      grid-column-end: 23;
      width: 100%;
    }
    .hesehus-storyboard-inspiration {
      grid-row-start: 68;
      grid-column-start: 2;
      grid-column-end: 12;
      width: 100%;
    }
    .hesehus-storyboard-fristads-kansas {
      grid-row-start: 68;
      grid-column-start: 13;
      grid-column-end: 23;
      width: 100%;
    }
  }
}
</style>
<script>
export default {
  name: "CasesProcess"
};
</script>
