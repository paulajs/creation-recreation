<template>
  <div class="misc">
    <div class="misc-header">
      <h1>Miscellaneous</h1>
      <HomeButton />
      <div class="misc-description">
        <div class="misc-background"></div>
        <p>Various random projects and experiments</p>
      </div>
    </div>
    <div class="misc-grid">
      <MiscCaseWrappedDouble
        miscCaseClass="misc-case1"
        headerClass="header-audio"
        headerFirstClass="text-audio"
        headerSecondClass="text-exp"
        headerFirstText="Audio"
        headerSecondText="experiments"
      >
        <component :is="case_audio_component"></component>
      </MiscCaseWrappedDouble>
      <MiscCaseSingle
        miscCaseClass="misc-case2"
        headerClass="header-space"
        headerText="Space Kitty"
        stars = "yes"
      >
        <component :is="case_space_component"></component>
      </MiscCaseSingle>
      <MiscCaseDouble
        miscCaseClass="misc-case3"
        headerOneClass="header-adams-ill"
        headerTwoClass="header-adams"
        headerOneText="illustration"
        headerTwoText="Dr Adams"
      >
        <component :is="case_adams_component"></component>
      </MiscCaseDouble>
      <MiscCaseDouble
        miscCaseClass="misc-case4"
        headerOneClass="header-bunny-left"
        headerTwoClass="header-bunny-right"
        headerOneText="Bunny"
        headerTwoText="Games"
      >
        <component :is="case_bunny_component"></component>
      </MiscCaseDouble>
      <MiscCaseWrappedDouble
        miscCaseClass="misc-case5"
        headerClass="header-three"
        headerFirstClass="text-three"
        headerSecondClass="text-exp"
        headerFirstText="Three js"
        headerSecondText="experiments"
      >
        <component :is="case_three_component"></component>
      </MiscCaseWrappedDouble>
      <MiscCaseSingle
        miscCaseClass="misc-case6"
        headerClass="header-ripple"
        headerText="Ripple effect"
        stars = "no"
      >
        <component :is="case_ripple_component"></component>
      </MiscCaseSingle>
      <MiscCaseWrappedDouble
        miscCaseClass="misc-case7"
        headerClass="header-css-anim"
        headerFirstClass="text-css"
        headerSecondClass="text-anim"
        headerFirstText="CSS"
        headerSecondText="animation"
      >
        <component :is="case_css_component"></component>
      </MiscCaseWrappedDouble>
      <MiscCaseSingle
        miscCaseClass="misc-case8"
        headerClass="header-horror"
        headerText="Horror game"
        stars ="yes"
      >
      <component :is="case_horror_component"></component>
      </MiscCaseSingle>
      <MiscCaseSingle
      miscCaseClass="misc-case9"
      headerClass="header-draw"
      headerText="drawings"
      stars ="no"
      >
        <component :is="case_draw_component"></component>
      </MiscCaseSingle>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import "@/assets/sass/_global.scss";
@import "@/assets/sass/_mixins.scss";

.misc-header {
  @include create-grid(4, 9.94vh, 12, 7.01vw, 1vh, 1vw);
  margin: 2vh 2vw 7vh 2vw;
  align-items: center;
  h1 {
    font-family: "Poppins", sans-serif;
    font-size: 7.6vw;
    width: 100%;
    color: black;
    @include place-in-grid(1, 4, 1, 10);
  }
  .home-button {
    @include place-in-grid(1, 4, 12, 12);
    justify-self: end;
  }
  .misc-description {
    @include place-in-grid(4, 5, 1, 13);
    height: 100%;
    background: $color-pink;
    border: 1px solid black;
    position: relative;
    p {
      color: white;
      font-family: $font-secundary;
      font-size: 1.5em;
      margin-left: 3vw;
      @include centerY();
      font-weight: 300;
    }
    .misc-background {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      background: linear-gradient(
        -45deg,
        $color-pink-light -70%,
        $color-green 120%
      );
      opacity: 0.6;
    }
  }
}
.misc-grid {
  @include create-grid(18, 11.94vh, 12, 5.18vw, 7vh, 3vw);
  display: grid;
  margin: 2vh 2vw;
}
</style>

<script>
import HomeButton from "@/components/HomeButton.vue";
import MiscCaseWrappedDouble from "@/views/partials/MiscCaseWrappedDouble.vue";
import MiscCaseSingle from "@/views/partials/MiscCaseSingle.vue";
import MiscCaseDouble from "@/views/partials/MiscCaseDouble.vue";
import MiscCaseAudioSVG from "@/components/svg/MiscCaseAudioSVG.vue";
import MiscCaseSpaceSVG from "@/components/svg/MiscCaseSpaceSVG.vue";
import MiscCaseAdamsSVG from "@/components/svg/MiscCaseAdamsSVG.vue";
import MiscCaseBunnySVG from "@/components/svg/MiscCaseBunnySVG.vue";
import MiscCaseThreeSVG from "@/components/svg/MiscCaseThreeSVG.vue";
import MiscCaseRippleSVG from "@/components/svg/MiscCaseRippleSVG.vue";
import MiscCaseCSSSVG from "@/components/svg/MiscCaseCSSSVG.vue";
import MiscCaseHorrorSVG from "@/components/svg/MiscCaseHorrorSVG.vue";
import MiscCaseDrawSVG from "@/components/svg/MiscCaseDrawSVG.vue";
export default {
  components: {
    HomeButton,
    MiscCaseWrappedDouble,
    MiscCaseSingle,
    MiscCaseDouble,
    MiscCaseAudioSVG,
    MiscCaseSpaceSVG,
    MiscCaseAdamsSVG,
    MiscCaseBunnySVG,
    MiscCaseThreeSVG,
    MiscCaseRippleSVG,
    MiscCaseCSSSVG,
    MiscCaseHorrorSVG,
    MiscCaseDrawSVG
  },
  data() {
    return {
      case_audio_component: "MiscCaseAudioSVG",
      case_space_component: "MiscCaseSpaceSVG",
      case_adams_component: "MiscCaseAdamsSVG",
      case_bunny_component: "MiscCaseBunnySVG",
      case_three_component: "MiscCaseThreeSVG",
      case_ripple_component: "MiscCaseRippleSVG",
      case_css_component: "MiscCaseCSSSVG",
      case_horror_component: "MiscCaseHorrorSVG",
      case_draw_component: "MiscCaseDrawSVG"
    };
  }
};
</script>

