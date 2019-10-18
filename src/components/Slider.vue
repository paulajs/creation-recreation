<template>
  <div class="slider">
    <div class="nav-right">
      <button class="nav-slider-button" v-on:click="next">
        <svg class="arrow-slider" viewBox="0 0 23.75 4.71">
          <polygon
            points="23.75 2.35 14.98 0 14.98 1.6 0 1.6 0 3.1 14.98 3.1 14.98 4.71 23.75 2.35"
          />
        </svg>
        <p class="nav-slider-button-text" data-text="Next">Next</p>
      </button>
    </div>
    <div class="image-container">
      <img
        v-for="(image, key) in images"
        v-bind:key="image.id"
        :src="image.path"
        :alt="image.altText"
        :class="(key == index ? 'active' + ' image-anim' : 'inactive')"
      />
    </div>
    <div class="nav-left">
      <button class="nav-slider-button" v-on:click="previous">
        <svg class="arrow-slider" viewBox="0 0 23.75 4.71">
          <polygon points="0 2.35 8.78 4.71 8.78 3.1 23.75 3.1 23.75 1.6 8.78 1.6 8.78 0 0 2.35" />
        </svg>
        <p class="nav-slider-button-text" data-text="Previous">Previous</p>
      </button>
    </div>
    <div class="nav-overview">
      <svg class="navigation-bar" viewBox="-10 0 262 31">
        <line x1="-5" y1="13.98" x2="248" y2="13.98" stroke="black"/>
        <circle
          v-for="(image, key) in images"
          v-bind:key="image.id"
          :class="'slide-indicator ' + (key == index ? 'slide-active-indicator' : '')"
          :cx="getIndicatorXPosition(key)"
          cy="13.98"
          r="8"
        />
      </svg>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import "../assets/sass/_global.scss";
.nav-slider-button {
  background: #000;
  border: none;
  border-radius: 100%;
  width: 70px;
  height: 70px;
  position: relative;
  border: none;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  p {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }
  &:hover .arrow-slider {
    display: none;
  }
  &:hover {
    cursor: pointer;
    border: 2px solid #ff00ff;
    background: white;
    transform: scale(1.2);
    transition: all 0.2s ease-in;
    &::after {
      border: 2px solid #00ff66;
      animation: rumble 0.3s ease-in 2;
    }

    .nav-slider-button-text::after {
      content: attr(data-text);
      position: absolute;
      color: #00ff66;
      left: 3%;
      top: 4%;
      animation: rumble 0.3s ease-in 2;
    }

    .nav-slider-button-text {
      color: #ff00ff;
    }
    svg.arrow {
      animation: arrowHide 0.2s ease forwards;
    }
    .nav-slider-button-text {
      animation: textShow 0.3s ease forwards;
      cursor: pointer;
    }
  }
  &::after {
    content: "";
    width: 70px;
    height: 70px;
    border: none;
    border-radius: 100%;
    background: transparent;
  }
  &:focus {
    outline: 0;
  }
}

.arrow-slider {
  width: 69%;
  fill: white;
  top: 50%;
  left: 50%;
  position: absolute;
  transform: translate(-50%, -50%);
  transition: all 0.2s ease-in;
}
.slide-indicator {
  fill: white;
  stroke: #000;
  stroke-miterlimit: 10;
  stroke-width: 1px;
}

.slide-active-indicator {
  fill: black;
}

.slider {
  grid-row-start: 6;
  grid-row-end: 19;
  grid-column-start: 2;
  grid-column-end: 24;
  display: grid;
  grid-template-columns: repeat(24, 4.1667%);
  grid-template-rows: repeat(16, 6.25%);
  display: grid;
  grid-template-columns: repeat(24, 4.1667%);
  grid-template-rows: repeat(20, 6.25%);
}
.nav-right {
  grid-column-start: 23;
  grid-row-start: 8;
}
.nav-left {
  grid-column-start: 2;
  grid-row-start: 8;
}
.image-container {
  grid-column-start: 4;
  grid-column-end: 22;
  grid-row-start: 1;
}
.image-container img {
  width: 100%;
  box-shadow: 17px 15px 18px #333;
}
.nav-overview {
  grid-column-start: 10;
  grid-column-end: 16;
  grid-row-start: 19;
}
.nav-slider-button-text {
  visibility: hidden;
  color: white;
  font-weight: 400;
  font-family: $font-secundary;
  font-size: 90%;
  position: absolute;
  top: 31%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.2s ease-in;
}
.active {
  display: inline;
}
.inactive {
  display: none;
}

.clickAnim {
  animation: buttonClickAnim 0.5s ease forwards;
}
.image-anim {
  transition: all 0.2s ease-in;
  animation: imgFade 0.4s ease-out;
}
@keyframes imgFade {
  0% {
    opacity: 0.2;
    transform: scale(0.995);
    box-shadow: 0px 0px 0px #333;
  }
  80% {
    transform: scale(1);
    opacity: 0.8;
  }
  100% {
    opacity: 1;
    box-shadow: 17px 15px 18px #333;
  }
}


@keyframes textShow {
  0% {
    visibility: visible;
    opacity: 0;
    transform: translate(-80px, -50%);
  }
  100% {
    visibility: visible;
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}

@keyframes arrowHide {
  0% {
    transform: scaleX(1) translate(-50%, -50%);
  }
  100% {
    transform: scaleX(0) translate(100%, -50%);
  }
}

@keyframes buttonClickAnim {
  0% {
    transform: scale(0.2);
    border: 1px solid black;
    background: black;
    opacity: 0.8;
  }
  50% {
    border: 30px solid black;
    background: black;
    opacity: 0.4;
  }
  90% {
    border: 10px solid black;
    opacity: 0.1;
    transform: scale(1.2);
  }
  100% {
    border: 1px solid black;
    opacity: 1;
  }
}
</style>
<script>
export default {
  name: "Slider",
  props: {
    images: Array,
  },
  data() {
    const radius= 8;
    const lengthOfLine = radius * 2 * this.images.length + (70 * this.images.length - 2);
    const x = lengthOfLine - 2 * parseInt(radius);
    const y = this.images.length - 2 + 1;

    return {
      index: 0,
      len: x / y,
    };
  },
  methods: {
    getIndicatorXPosition(index) {
      return this.len * index + index
    },
    next() {
      const index = this.index + 1;
      if (index == this.images.length) {
        this.index = 0;
      } else {
        this.index = index;
      }
    },
    previous() {
      const index = this.index - 1;
      if (index < 0) {
        this.index = this.images.length - 1;
      } else {
        this.index = index;
      }
    }
  }
};
</script>
