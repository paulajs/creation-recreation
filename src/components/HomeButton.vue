<template>
  <button class="home-button">
    <p class="home-button-text" data-text="Home" >Home</p>
  </button>
</template>
<style lang="scss" scoped>
$transition: all 0.1s ease-in;

.home-button {
  border-radius: 100%;
  width: 83px;
  height: 83px;
  border: none;
  background: black;
  color: white;
  font-family: "Poppins", sans-serif;
  font-size: 21px;
  font-weight: 800;
  transition: $transition;
  &:focus {
    outline: 0;
  }
  p {
    position: relative;
    transition: $transition;
  }
  &:hover {
    transition: $transition;
    transform: scale(1.1);
    cursor: pointer;
  }
  &:hover p {
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: #ff00ff;
    transform-origin: center;
  }
  &:hover p:after {
    content: attr(data-text);
    left: 8.5px;
    top: 0.5px;
    position: absolute;
    color: transparent;
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: #00ff66;
    animation: rumble 0.3s ease-in infinite;
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
  96% {
    border: 10px solid black;
    opacity: 0.1;
    background: black;
    transform: scale(1.2);
  }
  100% {
    border: 1px solid black;
    opacity: 1;
    background: white;
    transform: scale(1.2);
  }
}
</style>
<script>

export default {
  name: "HomeButton",
};
</script>
