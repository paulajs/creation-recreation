<template>
  <div class="slider">
    <div class="nav-right">
      <button class="nav-slider-button" data-direction="right" v-on:click="sliderButtonHandler">
        <svg class="arrow-slider" viewBox="0 0 23.75 4.71">
          <title>arrow right</title>
          <polygon
            points="23.75 2.35 14.98 0 14.98 1.6 0 1.6 0 3.1 14.98 3.1 14.98 4.71 23.75 2.35"
          />
        </svg>
        <p class="nav-slider-button-text" data-text="Next">Next</p>
      </button>
    </div>
    <div class="image-container">
      <img src="../assets/img/nmg-premium.jpg" class="active" data-active="true" alt="nmg-img" />
      <img src="../assets/img/nmg-retro.jpg" class="inactive" data-active="false" alt="nmg-img" />
      <img src="../assets/img/mood-nmg-100.jpg" class="inactive" data-active="false" alt="nmg-img" />
    </div>
    <div class="nav-left">
      <button class="nav-slider-button" data-direction="left" v-on:click="sliderButtonHandler">
        <svg class="arrow-slider" viewBox="0 0 23.75 4.71">
          <title>arrow left</title>
          <polygon points="0 2.35 8.78 4.71 8.78 3.1 23.75 3.1 23.75 1.6 8.78 1.6 8.78 0 0 2.35" />
        </svg>
        <p class="nav-slider-button-text" data-text="Previous">Previous</p>
      </button>
    </div>
    <div class="nav-overview">
      <svg class="navigation-bar" viewBox="-10 0 262 31">
        <title>nav-overview-slider</title>
        <line x1="-5" y1="13.98" x2="248" y2="13.98" stroke="black"/>
        <circle v-for="posX in posXArray" v-bind:key="posX.id" class="cls-1 item" :cx= "posX" cy="13.98" r="8" />
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
.cls-1 {
  fill: white;
  stroke: #000;
  stroke-miterlimit: 10;
  stroke-width: 1px;
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
  data() {
    const prefix= "../assets/img/";
    const imgArray= ["nmg-premium.jpg", "nmg-retro.jpg", "mood-nmg-100.jpg"];
    const radius= 8;
    const lengthOfLine = radius * 2 * imgArray.length + (70 * imgArray.length - 2);
    const x = lengthOfLine - 2 * parseInt(radius);
    const y = imgArray.length - 2 + 1;
    const len = x / y;
    const posXArray = [len * 0 + parseInt(0), len * 1 + parseInt(1), len * 2 + parseInt(2)];

    return {
      prefix: prefix,
      imgArray: imgArray,
      index: 0,
      currentButton: null,
      radius: radius,
      lengthOfLine: lengthOfLine,
      x : x,
      y: y,
      len: len,
      posXArray: posXArray,
    };
  },
  mounted(){
    this.init();
  },
  methods: {
    init: function(){
      let circleActive = document.querySelectorAll(".item")[0];
      circleActive.style.fill = "black";
    },
    sliderButtonHandler: function(e) {
      this.clickedButton(e);
      const buttonText = this.currentButton.querySelector(
        ".nav-slider-button-text"
      );
      this.sliderButtonAddAnimation(buttonText);
      this.sliderButtonRemoveAnimation(buttonText);
      console.log(this.currentButton.dataset);
      if (this.currentButton.dataset.direction == "right") {
        this.changeImage(this.changeNext);
      } else {
        this.changeImage(this.changePrev);
      }
    },
    sliderButtonAddAnimation: function(buttonText) {
      buttonText.style.display = "none";
      this.currentButton.classList.add("clickAnim");
    },
    sliderButtonRemoveAnimation: function(buttonText) {
      setTimeout(() => {
        this.currentButton.classList.remove("clickAnim");
        buttonText.style.display = "block";
        let imageSliderImg = document
          .querySelector(".image-container img")
          .classList.remove("image-anim");
      }, 400);
    },
    clickedButton: function(e) {
      if (e.target.tagName == "P") {
        this.currentButton = e.target.parentElement;
      } else {
        this.currentButton = e.target;
      }
    },
    changeImage: function(func) {
      const sliderImgArray= document.querySelector(".image-container").children;
      for (let i = 0; i < sliderImgArray.length; i++) {
        if (sliderImgArray[i].dataset.active == "true") {
          func(i, sliderImgArray);
        }
      }
      this.setData(sliderImgArray);
      this.setStylingFromData(sliderImgArray);
    },
    setData: function(sliderImgArray) {
      for (let i = 0; i < sliderImgArray.length; i++) {
        sliderImgArray[i].dataset.active = "false";
      }
      sliderImgArray[this.index].dataset.active = "true";
    },
    setStylingFromData: function(sliderImgArray) {
      for (let i = 0; i < sliderImgArray.length; i++) {
        sliderImgArray[i].classList = "";
        sliderImgArray[i].classList.add("inactive");
      }
      sliderImgArray[this.index].classList.replace("inactive", "active");
      sliderImgArray[this.index].classList.add("image-anim");
    },
    changeNext: function(i, sliderImgArray) {
      this.index = i + 1;
      if (this.index == sliderImgArray.length) {
        this.index = 0;
      }
      this.fillNavCircle(this.index);
    },
    changePrev: function(i, sliderImgArray) {
      this.index = i - 1;
      if (this.index < 0) {
        this.index = sliderImgArray.length - 1;
      }
      this.fillNavCircle(this.index);
    },
    fillNavCircle: function(index) {
      let circles = document.querySelectorAll(".item");
      for (let j = 0; j < circles.length; j++) {
        circles[j].style.fill = "white";
      }
      circles[this.index].style.fill = "black";
    }
  }
};
</script>
