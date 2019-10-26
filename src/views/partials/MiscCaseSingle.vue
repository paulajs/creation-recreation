<template>
  <div :class="miscCaseClass">
    <div class="misc-background"></div>
    <img :class="stars" src="../../assets/img/SVG/stars.svg" alt="stars">
    <div :class="headerClass">
      <h2>{{headerText}}</h2>
    </div>
    <slot></slot>
  </div>
</template>
<style lang="scss" scoped>
@import "@/assets/sass/_global.scss";
@import "@/assets/sass/_mixins.scss";
div {
  .misc-background {
    width: 100%;
    height: 100%;
  }
}
.yes{
  position: absolute;
  top: 0;
  display: block;
}
.no{
  position: absolute;
  top: 0;
  display: none;
}
.misc-case2 {
  @include place-in-grid(1, 5, 4, 10);
  background: $color-pink;
  border: 1px solid black;
  position: relative;
  .header-space {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    background: $color-pink;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: 1px solid black;
    h2 {
      @include header-style(uppercase);
      font-size: 4vw;
    }
  }
  .misc-background {
    @include misc-background(bottom, -70%, 120%, 0.7);
  }
}
  .misc-case6 {
    @include place-in-grid(5, 9, 10, 13);
    background: $color-pink;
    border: 1px solid black;
    position: relative;
    .header-ripple {
      @include header-style(none);
      position: absolute;
      top: 3vh;
      left: 2vw;
      font-size: 2.4vw;
      width: 50%;
      line-height: 4.6vw;
    }
    .misc-background {
      @include misc-background(right, -70%, 150%, 0.7);
    }
  }
  .misc-case8 {
    @include place-in-grid(9, 13, 4, 10);
    background: $color-pink;
    border: 1px solid black;
    position: relative;
    .header-horror {
      @include header-style(uppercase);
      position: absolute;
      padding: 0.5vh 0;
      top: 0;
      width: 100%;
      background: $color-green-dark;
      text-align: center;
      font-size: 2.3vw;
      border-bottom: 1px solid black;
    }
    .misc-background {
      @include misc-background(top, -60%, 100%, 0.6);
    }
  }

  .misc-case9 {
    @include place-in-grid(9, 13, 10, 13);
    background: $color-green;
    border: 1px solid black;
    position: relative;
    .header-draw {
      @include header-style(uppercase);
      @include centerX();
      background: $color-green;
      border: 1px solid black;
      position: absolute;
      top: 3vh;
      width: 86%;
      text-align: center;
      font-size: 1.8vw;
    }
    .misc-background {
      @include misc-background(right, 0%, 110%, 0.6);
    }
  }
</style>
<script>
export default {
  name: "MiscCaseSingle",
  props: {
    miscCaseClass: String,
    headerClass: String,
    headerText: String,
    stars: String
  }
};
</script>
