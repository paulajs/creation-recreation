<template>
  <div :class="sectionClass">
    <div :class="sectionHeaderClass">
      <h5>{{headertext}}</h5>
    </div>
    <p :class="textClass">{{sectionText}}</p>
  </div>
</template>
<style lang="scss" scoped>
.case-text-section {
  display: grid;
  grid-template-rows: repeat(90, 4.94vh);
  grid-row-gap: 1vh;
  grid-template-columns: repeat(24, 3.125vw);
  grid-column-gap: 1vw;
  .case-section-header {
    color: white;
    background: black;
    grid-column-end: 6;
    display: grid;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    height: 3.06vh;
    transform: translateX(-1vw);
    grid-column-start: 1;
    h5 {
      grid-column-start: 2;
      align-self: center;
      font-size: 18px;
      transform: translateX(1vw);
      font-weight: 300;
      grid-row-start: 1;
    }
  }
  p {
    grid-column-start: 2;
    grid-column-end: 6;
    grid-row-start: 2;
  }
  .inspiration-text-nmg {
    grid-column-end: 8;
}
p.experimentation-text-nmg {
    grid-column-end: 12;
}
p.experimentation-text-hesehus {
    grid-column-end: 8;
}
}
</style>
<script>
export default {
  name: "CaseTextSection",
  props: {
    sectionClass: String,
    sectionHeaderClass: String,
    headertext: String,
    textClass: String,
    sectionText: String
  }
};
</script>
