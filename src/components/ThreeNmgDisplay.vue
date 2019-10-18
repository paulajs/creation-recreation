<template>
  <div class="display-nmg">
    <div class="displayImgBackgroundOpacity"></div>
    <p class="nmg-result-para">
      The resulting illustrations symbolises marmalade splatter dropped on floor like children's playfulness in the kitchen, where accidents sometimes happen ;).
      The splatter is combined with a focus on each of the main ingredients in the marmalade, and which are grown on the farm.
      Results are illustrated with interactive 3d, you can zoom, pan and click to open the folder.
    </p>
    <div class="result-nmg-wrapper">
      <NMGDisplayGif
        displayID ="strawberryjam"
        imgClass ="resultDisplay"
        :displayImgSrc="getStrawberryJamGif()"
        displayImgAlt="strawberry jam"
      />
       <NMGDisplayGif
        displayID ="strawberryfolder"
        imgClass ="resultDisplay"
        :displayImgSrc="getStrawberryFolderGif()"
        displayImgAlt="strawberry folder"
      />
       <NMGDisplayGif
        displayID ="quincejam"
        imgClass ="resultDisplay"
        :displayImgSrc="getQuinceJamGif()"
        displayImgAlt="quince jam"
      />
      <NMGDisplayGif
        displayID ="quincefolder"
        imgClass ="resultDisplay"
        :displayImgSrc="getQuinceFolderGif()"
        displayImgAlt="quince folder"
      />

      <NMGDisplayGif
        displayID ="elderjam"
        imgClass ="resultDisplay"
        :displayImgSrc="getElderJamGif()"
        displayImgAlt="elder jam"
      />

       <NMGDisplayGif
        displayID ="elderfolder"
        imgClass ="resultDisplay"
        :displayImgSrc="getElderFolderGif()"
        displayImgAlt="elder folder"
      />

    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/sass/_global.scss";
.display-nmg {
  grid-column-start: 2;
  grid-column-end: 23;
  grid-row-start: 17;
  .nmg-result-para {
    font-family: $font-secundary;
  }
  .result-nmg-wrapper {
    display: grid;
    grid-template-rows: repeat(30, 4.94vh);
    grid-row-gap: 1vh;
    grid-template-columns: repeat(22, 3.125vw);
    grid-column-gap: 1vw;

    .resultDisplay {
      width: 100%;
      border: 2px solid black;
    }
    #strawberryjam {
      grid-column-start: 2;
      grid-column-end: 11;
      position: relative;
      grid-row-start: 2;
      grid-row-end: 10;
    }
    #strawberryfolder {
      grid-column-start: 12;
      grid-column-end: 21;
      position: relative;
      grid-row-start: 2;
      grid-row-end: 10;
    }
    #quincejam {
      grid-column-start: 2;
      grid-column-end: 11;
      position: relative;
      grid-row-start: 11;
      grid-row-end: 19;
    }
    #quincefolder {
      grid-column-start: 12;
      grid-column-end: 21;
      position: relative;
      grid-row-start: 11;
      grid-row-end: 19;
    }
    #elderjam {
      grid-column-start: 2;
      grid-column-end: 11;
      position: relative;
      grid-row-start: 20;
      grid-row-end: 28;
    }
    #elderfolder {
      grid-column-start: 12;
      grid-column-end: 21;
      position: relative;
      grid-row-start: 20;
      grid-row-end: 28;
    }
  }
}
</style>
<script>
import * as THREE from "three";
import * as OrbitControls from "three-orbitcontrols";
import GLTFLoader from "three-gltf-loader";

import NMGDisplayGif from "@/components/NMGDisplayGif.vue";
const strawberryjam = require("../assets/img/display/strawgif1.gif");
const strawberryfolder = require("../assets/img/display/strawfolderGif1.gif");
const quincejam = require("../assets/img/display/kvadgif1.gif");
const quincefolder = require( "../assets/img/display/kvadfolderGif1.gif");
const elderjam = require("../assets/img/display/hyldgif1.gif");
const elderfolder = require("../assets/img/display/hyldfolderGif1.gif")

//https://medium.com/@matthewmain/how-to-import-a-3d-blender-object-into-a-three-js-project-as-a-gltf-file-5a67290f65f2
export default {
  name: "ThreeNmgDisplay",
  components: {
    NMGDisplayGif,
  },
  methods: {
    getStrawberryJamGif: () => strawberryjam,
    getStrawberryFolderGif: () => strawberryfolder,
    getQuinceJamGif: () => quincejam,
    getQuinceFolderGif: () => quincefolder,
    getElderJamGif: () =>  elderjam,
    getElderFolderGif: () =>  elderfolder,
  },
  mounted() {
    console.log("mounted");
    //this.init();
  }
};
</script>
