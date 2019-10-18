<template>
  <div class="cases-result-hesehus">
    <ButtonVisitPage />
    <div class="display-results">
      <h2 class="result-header">Videos</h2>
      <VideoCaseComponent
        videoSection="video-section section-matas"
        videoName="Matas Video"
        :videoSrc="getMatasVideo()"
        :videoPoster="getMatasPoster()"
      />
      <VideoCaseComponent
        videoSection="video-section section-fristads"
        videoName="Fristads Kansas Video"
        :videoSrc="getFristadsVideo()"
        :videoPoster="getFristadsPoster()"
      />
      <VideoCaseComponent
        videoSection="video-section section-inspiration"
        videoName="Inspiration Video"
        :videoSrc="getInspirationVideo()"
        :videoPoster="getInspirationPoster()"
      />
      <VideoCaseComponent
        videoSection="video-section section-danoffice"
        videoName="Danoffice Video"
        :videoSrc="getDanofficeVideo()"
        :videoPoster="getDanofficePoster()"
      />
      <VideoCaseComponent
        videoSection="video-section section-kunderejse"
        videoName="Customer journey Video"
        :videoSrc="getJourneyVideo()"
        :videoPoster="getJourneyPoster()"
      />
      <div class="mockup-hesehus">
        <h4>Mockup of the React.js app.</h4>
        <img src="../assets/img/hesehus-app-mock.png" alt />
      </div>
    </div>
  </div>
</template>
<style lang="scss">
@import "../assets/sass/_global.scss";

$transition: all 0.1s ease-in;

.cases-result-hesehus {
  display: flex;
  flex-direction: column;
  align-items: center;
  .display-results {
    display: grid;
    grid-template-rows: repeat(133, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    padding: 2vh 0.55vw;
    background: white;
    h2.result-header {
      grid-column-start: 2;
      grid-column-end: 24;
      grid-row-start: 1;
      grid-row-end: 4;
      font-family: $font-primary;
      transform: translateY(-184px) translateX(-17.068px);
      font-size: 150px;
      color: black;
    }
    .mockup-hesehus {
      grid-row-start: 109;
      grid-row-end: 131;
      grid-column-start: 1;
      grid-column-end: 25;
      background: linear-gradient(#ff90ff, #00ffc8);
      display: flex;
      flex-direction: column;
      border: 1px solid black;
      h4 {
        margin-left: 4.75vw;
        margin-top: 4vh;
        font-family: $font-primary;
        font-size: 87px;
        color: white;
        -webkit-text-stroke-width: 1px;
        -webkit-text-stroke-color: black;
      }
      img {
        width: 80%;
        align-self: center;
        margin-top: 7vh;
      }
    }
  }
}
</style>
<script>
import VideoCaseComponent from "@/components/VideoCaseComponent.vue";
import ButtonVisitPage from "@/components/ButtonVisitPage.vue";

const matasVideo = require("../assets/videos/hesehus/Matas1.mp4");
const matasPoster = require("../assets/videos/hesehus/Matas1.png");
const fristadsVideo = require("../assets/videos/hesehus/Fristads-kansas1.mp4");
const fristadsPoster = require("../assets/videos/hesehus/Fristads-kansas1.png");
const inspirationVideo = require("../assets/videos/hesehus/Inspiration1.mp4");
const inspirationPoster = require("../assets/videos/hesehus/Inspiration1.png");
const danofficeVideo = require("../assets/videos/hesehus/Danoffice1.mp4");
const danofficePoster = require("../assets/videos/hesehus/Danoffice1.png");
const journeyVideo = require("../assets/videos/hesehus/Kunderejse1.mp4");
const journeyPoster = require("../assets/videos/hesehus/Kunderejse1.png");
export default {
  name: "CasesResultHesehus",
  methods: {
    getMatasVideo: () => matasVideo,
    getMatasPoster: () => matasPoster,
    getFristadsVideo: () => fristadsVideo,
    getFristadsPoster: () => fristadsPoster,
    getInspirationVideo: () => inspirationVideo,
    getInspirationPoster: () => inspirationPoster,
    getDanofficeVideo: () => danofficeVideo,
    getDanofficePoster: () => danofficePoster,
    getJourneyVideo: () => journeyVideo,
    getJourneyPoster: () => journeyPoster
  },
  components: {
    VideoCaseComponent,
    ButtonVisitPage
  }
};
</script>
