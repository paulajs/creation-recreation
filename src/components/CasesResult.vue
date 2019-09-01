<template>
  <div class="cases-result">
    <button class="visit-page">
      <p>Visit page</p>
    </button>
    <div class="display-results">
      <h2 class="result-header">Videos</h2>
      <div class="video-section">
        <div class="video-section-header">
          <h4 class="matas-header">Matas video</h4>
        </div>
        <video class="case-video" src="../assets/videos/hesehus/Matas1.mp4"></video>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.cases-result {
  display: flex;
  flex-direction: column;
  align-items: center;
  .visit-page {
    width: 320px;
    height: 70px;
    margin-bottom: 20vh;
  }
  .display-results {
    display: grid;
    grid-template-rows: repeat(60, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    margin: 2vh 1vw;
    h2.result-header {
      grid-column-start: 2;
      grid-column-end: 6;
      grid-row-start: 1;
      font-family: "Poppins", sans-serif;
      font-size: 87px;
      color: black;
    }
    .video-section {
      grid-row-start: 4;
      display: grid;
      grid-template-rows: repeat(18, 4.94vh);
      grid-row-gap: 1vh;
      grid-template-columns: repeat(24, 3.125vw);
      grid-column-gap: 1vw;
      .video-section-header {
        color: white;
        background: black;
        grid-column-start: 1;
        grid-column-end: 5;
        display: grid;
        grid-template-columns: repeat(24, 3.125vw);
        grid-column-gap: 1vw;
        height: 3.06vh;
        transform: translateX(-1vw);
        font-family: "Source Code Pro", monospace;
        .matas-header {
          grid-row-start: 2;
          grid-column-start: 2;
          align-self: center;
          font-size: 18px;
          transform: translateX(1vw);
          font-weight: 300;
        }
      }
      .case-video {
        grid-row-start: 3;
        grid-column-start: 4;
        grid-column-end: 22;
        width: 100%;
      }
    }
  }
}
</style>
<script>
export default {
  name: "CasesResult"
};
</script>
