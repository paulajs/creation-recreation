<template>
  <div class="case-process-hesehus">
    <h2>Process</h2>
    <div class="process-wrapper">
       <CaseTextSection
        sectionClass = "case-text-section inspiration-hesehus"
        sectionHeaderClass="case-section-header"
        headertext="Inspiration"
        textClass="inspiration-text-hesehus"
        sectionText="Moodboard of Hesehus’ visual identity and research of e-commerce fairs."
      />

      <img class="hesehus-indtryk" src="../assets/img/hesehus-indtryk.jpg" alt />
      <img class="hesehus-messe" src="../assets/img/hesehus-messe.jpg" alt />
      <CaseTextSection
        sectionClass = "case-text-section experimentation-hesehus"
        sectionHeaderClass="case-section-header header-experimentation-hesehus"
        headertext="Experimentation"
        textClass="experimentation-text-hesehus"
        sectionText=" Work process/ customer journey represented by boat and by spaceship, and
        development of graphic universe for the cases."
      />

      <img class="hesehus-boat" src="../assets/img/hesehus-boat.png" alt />
      <img class="hesehus-space" src="../assets/img/hesehus-space.png" alt />
      <img class="hesehus-ideation" src="../assets/img/hesehus-ideation.jpg" alt />

      <CaseTextSection
        sectionClass = "case-text-section storyboards-hesehus"
        sectionHeaderClass="case-section-header header-storyboards-hesehus"
        headertext="Storyboards"
        textClass="storyboards-text-hesehus"
        sectionText=" Example of a storyboard for the case Inspiration."
      />
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
.case-process-hesehus {
  h2{
    font-family: "Poppins", sans-serif;
    font-size: 150px;
    color: black;
    margin-left: 4.75vw;
    margin-top: 4vh;
  }
  .process-wrapper {
    grid-row-start: 3;
    font-family: "Source Code Pro", monospace;
    display: grid;
    grid-template-rows: repeat(90, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    margin: 0 1vw;

    .inspiration-hesehus{
      grid-row-start: 2;
      grid-column-start: 1
    }
    .experimentation-hesehus{
      grid-row-start: 21;
      grid-column-start: 1
    }
    .storyboards-hesehus{
      grid-row-start: 63;
      grid-column-start: 1
    }

    p {
      grid-column-start: 2;
      grid-column-end: 6;
    }
    .hesehus-indtryk {
      grid-row-start: 6;
      grid-column-start: 2;
    }
    .hesehus-messe {
      grid-row-start: 6;
      grid-column-start: 14;
      height: 635px;
    }
    .hesehus-boat {
      grid-row-start: 25;
      grid-column-start: 4;
      height: 91vh;
    }
    .hesehus-space {
      grid-row-start: 25;
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
      grid-row-start: 67;
      grid-column-start: 2;
      grid-column-end: 12;
      width: 100%;
    }
    .hesehus-storyboard-fristads-kansas {
      grid-row-start: 67;
      grid-column-start: 13;
      grid-column-end: 23;
      width: 100%;
    }
  }
}
</style>
<script>
import CaseTextSection from "@/components/CaseTextSection.vue";
export default {
  name: "CasesProcessHesehus",
  components: {
    CaseTextSection,
  }
};
</script>
