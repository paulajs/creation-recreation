<template>
  <div class="cases-result">
    <button class="visit-page">
      <p data-text="Visit page">Visit page</p>
    </button>
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
    </div>
  </div>
</template>
<style lang="scss">
$transition: all 0.1s ease-in;
$gradient: linear-gradient(#319fd1, #64eca9);
$font-primary: "Poppins", sans-serif;
$font-secundary: "Source Code Pro", monospace;
$color-green: #28ff7e;
$color-pink: #ff00ff;

.cases-result {
  display: flex;
  flex-direction: column;
  align-items: center;
  .visit-page {
    width: 320px;
    height: 70px;
    margin-bottom: 30vh;
    border: 2px solid black;
    background: white;
    font-family: $font-secundary;
    font-size: 18px;
    position: relative;
    &::before {
      content: "";
      width: 320px;
      height: 70px;
      border: 2px solid black;
      transform: translate(-150px, -12px);
      position: absolute;
      z-index: -1;
      transition: $transition;
    }
    &:hover::before {
      background: $gradient;
      transition: $transition;
    }
    &:focus {
      outline: 0;
    }
    &:hover {
      cursor: pointer;
      background: black;
      color: white;
      transition: $transition;
    }
    &:hover p{
      color: $color-pink;
      transform-origin: center;
    }
    &:hover p:after{
      content:attr(data-text);
        position: absolute;
        left: 102px;
        color: $color-green;
        animation: rumble 0.3s ease-in infinite;
    }
  }

  .display-results {
    display: grid;
    grid-template-rows: repeat(110, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(24, 3.125vw);
    grid-column-gap: 1vw;
    padding: 2vh 0.55vw;
    background: $gradient;
    h2.result-header {
      grid-column-start: 2;
      grid-column-end: 6;
      grid-row-start: 1;
      font-family: $font-primary;
      font-size: 87px;
      color: white;
      transform: translateY(-184px) translateX(-17.068px);
      font-size: 150px;
      color: #319fd1;
    }
  }
}
@keyframes rumble{
  0%{
    transform: translate3D(0px, 0px,0);
  }
  10%{
    transform: translate3D(0.5px, 0.5px,0);
  }
  40%{
    transform: translate3D(0px, 0px,0);
  }
  60%{
    transform: translate3D(-0.5px, 0.5px,0);
  }
  80%{
    transform: translate3D(0px, 0.5px,0);
  }
  100%{
    transform: translate3D(0.5px, 0px,0);
  }
}
</style>
<script>
import VideoCaseComponent from "@/components/VideoCaseComponent.vue";

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
  name: "CasesResult",
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
    VideoCaseComponent
  }
};
</script>
