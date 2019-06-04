<template>
  <div class="hello">
    <img class="page-logo" alt="page logo" src="../assets/img/SVG/logo.svg">
    <div id="container">
      <p class="pointsDisplay"></p>
      <audio id="bubbleSounds" src></audio>
      <video
        src
        id="full-screen-win"
        type="video/mp4"
        preload="auto"
        loop
        muted
        disableRemotePlayback
      ></video>
    </div>
  </div>
</template>

<script>
import * as THREE from "three";
import * as TWEEN from "tween";
import {ExplodeAnimation} from '../functions/explosion.js'

export default {
  name: "FrontpageEntertainment",
  data() {
    return {
      camera: null,
      scene: null,
      renderer: null,
      isAnimating: false,
      clickTime: Date.now(),
      newClick: this.clickTime + 1600,
      gameEnd: false,
      parts: [],
      dirs: [],
      particles: null,
      movementSpeed: 80,
      pointsDisplay: document.querySelector(".pointsDisplay"),
      //backWin: document.querySelector('#full-screen-win'),
      colorArray: [
        0xff00ff,
        0xff1aff,
        0xff33ff,
        0xff4dff,
        0xff66ff,
        0xff7fff,
        0x14f459,
        0x2eff73,
        0x47ff8c,
        0x61ffa6,
        0x7affbf,
        0x93ffd8,
        0xcc00cc,
        0xb300b3
      ]
    };
  },
  methods: {
    init: function() {
      if (window.innerWidth >= 736) {
        this.initiateCanvasDesktop();
      } else {
        //initiateCanvasMobile();
      }
    },
    createScene: function(distance, numBallsX, numBallsY, xMin, yMin, radius) {
      this.scene = new THREE.Scene();
      this.scene.fog = new THREE.FogExp2(0xcccccc, 0.0026);
      this.addRenderer();
      this.addCamera(0, 0, 390);

      this.addLight(0xffffff, 50, 200, 200);
      this.addLight(0xff00ff, 20, 500, -600);
      this.addLight(0x14f459, 300, 300, 50);

      this.AddGameBall(xMin, yMin, numBallsX, numBallsY, distance, radius);

      var geometry = new THREE.PlaneGeometry(200, 200, 32);
      var material = new THREE.MeshBasicMaterial({
        color: 0xffff00,
        side: THREE.DoubleSide
      });
    },
    initiateCanvasDesktop: function() {
      this.createScene(62, 11, 3, -330, -110, 20); /*9, 3*/
      //distance, numBallsX, numBallsY, xMin, yMin, radius
      this.animate();
      var canvas = document.querySelector("#container");
      canvas.addEventListener("mousedown", this.onDocumentMouseDown, false);
      canvas.addEventListener("mousemove", this.onDocumentMouseMove, false);
    },
    addRenderer: function() {
      this.renderer = new THREE.WebGLRenderer({ alpha: true });
      this.renderer.setSize(window.innerWidth, window.innerHeight);
      this.renderer.setPixelRatio(window.devicePixelRatio);
      this.renderer.setClearColor(0x000000, 0);
      var canvascon = document.querySelector("#container");
      canvascon.appendChild(this.renderer.domElement);
    },
    addCamera: function(posX, posY, posZ) {
      this.camera = new THREE.PerspectiveCamera(
        60,
        window.innerWidth / window.innerHeight,
        1,
        10000
      );
      this.camera.position.set(posX, posY, posZ); //450
      this.scene.add(this.camera);
    },
    addLight: function(color, posX, posY, posZ) {
      var light = new THREE.SpotLight(color);
      light.position.set(posX, posY, posZ);
      this.scene.add(light);
    },
    AddGameBall: function(xMin, yMin, numBallsX, numBallsY, distance, radius) {
      var xMax = xMin + numBallsX * distance;
      var yMax = yMin + numBallsY * distance;
      var count = 0;
      for (var i = xMin; i <= xMax; i += distance) {
        for (var j = yMin; j <= yMax; j += distance) {
          var objName = String(i) + String(j);
          this.makeAddSphere(0xffffff, i, j, 0, radius, objName, count);
          count = count + 1;
        }
      }
    },
    makeAddSphere: function(color, posX, posY, posZ, radius, name, delay) {
      var geometry = new THREE.SphereGeometry(radius, 16, 16);
      var material = new THREE.MeshPhongMaterial({
        color: color,
        transparent: true,
        opacity: 0.8
      });
      var mesh = new THREE.Mesh(geometry, material);
      mesh.position.x = posX;
      mesh.position.y = posY;
      mesh.position.z = posZ;
      mesh.name = name;
      mesh.scale.set(0.1, 0.1, 0.1);
      mesh.geometry.computeBoundingBox();
      new TWEEN.Tween(mesh.scale)
        .to(
          {
            x: 1,
            y: 1,
            z: 1
          },
          800
        )
        .delay(30 * delay)
        .easing(TWEEN.Easing.Elastic.Out)
        .start();
      this.scene.add(mesh);
    },
    onDocumentMouseMove: function(event) {
      if (this.isAnimating === false) {
        let intersects = this.getIntersects(event);
        if (intersects.length > 0) {
          this.mouseMoveSetColor(intersects[0].object.material);
          document.body.style.cursor = "pointer";
          let num = 2.2 * Math.random() + 0.5;
          this.scaleAnimation(intersects[0].object, num, 2500);
        } else {
          document.body.style.cursor = "default";
        }
      }
    },
    onDocumentMouseDown: function(event) {
      this.isAnimating = true;
      if (Date.now() < this.newClick) {
        return;
      }
      if (this.gameEnd == true) {
        this.gameEnded();
      }
      this.clickTime = Date.now();
      this.newClick = this.clickTime + 1600;

      //sounds.src = "/assets/" + "pop6" + ".mp3";

      document.querySelector(".pointsDisplay").style.animation = "none";
      let intersects = this.getIntersects(event);
      let scene = this.scene;
      let pointsDisplay = document.querySelector(".pointsDisplay");

      if (intersects.length > 0) {
        let array = this.getIntersectingBalls(intersects[0].object);
        this.scaleAnimation(intersects[0].object, 10, 700);
        //sounds.play();
        setTimeout(() => {
          this.isAnimating = false;

          scene.remove(intersects[0].object);
          this.bubblePopDesktop(pointsDisplay, array, event, intersects);
        }, 700);
      } else {
        this.isAnimating = false;
      }
    },
    getIntersectingBalls: function(intersectedObject) {
      let id = intersectedObject.name;
      let ball1BBox = new THREE.Box3(new THREE.Vector3(), new THREE.Vector3());
      ball1BBox.setFromObject(intersectedObject);
      let intersectArray = [];
      for (let i = 0; i < this.scene.children.length; i++) {
        if (this.scene.children[i].type == "Mesh" && id != this.scene.children[i].name) {
          let ball = this.scene.children[i];
          let ball2BBox = new THREE.Box3(
            new THREE.Vector3(),
            new THREE.Vector3()
          );
          ball2BBox.setFromObject(ball);
          if (ball1BBox.intersectsBox(ball2BBox)) {
            intersectArray.push(ball.name);
          }
        }
      }
      return intersectArray;
    },
    gameEnded: function() {
      this.gameEnd = false;
      console.log("end of game");
      //backWin.src = "";
      while (this.scene.children.length > 0) {
        this.scene.remove(scene.children[0]);
      }
      /*let bubblesElem = document.querySelector("#bubbles-container");
      let bubblesOldCanvas = bubblesElem.children[0];
      bubblesElem.removeChild(bubblesOldCanvas);
      if (window.innerWidth >= 736) {
        initiateCanvasDesktop();
      } else {
        initiateCanvasMobile();
      }*/
    },
    bubblePopDesktop: function(elem, array, e, intersects) {
      this.displayPoints(elem, array, e, e.clientX + "px", e.clientY + "px");
      this.removeBallsDesktop(array);
      this.addFireworks(intersects, 150, 100 + 300 * array.length, this.scene, this.dirs);
    },
    displayPoints: function(elem, array, e, posX, posY) {
      let points = (array.length + 1) * 1000;
      let backgrounds = [
        "../assets/bubbles/assets/points-background1.svg",
        "../assets/bubbles/assets/points-background2.svg",
        "../assets/bubbles/assets/points-background3.svg"
      ];
      let randomNum = Math.floor(Math.random() * 3);
      let str = "+" + String(points);
      elem.innerHTML = str;
      elem.style.left = posX;
      elem.style.top = posY;
      elem.style.color = "#fff";
      elem.style.webkitTextStroke = "1px #000";
      elem.style.background =
        "url('" + backgrounds[randomNum] + "') no-repeat top left";
      elem.style.animation = "pointsAnim 1.25s ease-in";
    },
    removeBallsDesktop: function(array) {
      for (let i = 0; i < array.length; i++) {
        for (let j = 0; j < this.scene.children.length; j++) {
          if (array[i] == this.scene.children[j].name) {
            this.scene.remove(this.scene.children[j]);
          }
        }
      }
      this.congratulate(0);
    },
    congratulate: function(minBall) {
      if (this.countBalls() === minBall) {
        this.congrats();
        gameEnd = true;
      }
    },
    congrats: function() {
      let sti = "assets/applause.mp4";
      let stiMob = "assets/applausemob.mp4";

      setTimeout(function() {
        if (window.innerWidth < 736) {
          //backWin.src = stiMob;
          //backWin.play();
        } else {
          //backWin.src = sti;
          //backWin.play();
        }
        //sounds.src = "assets/" + "applause" + ".wav";
        //sounds.play();
      }, 500);
    },
    countBalls: function() {
      let count = 0;
      for (var i = 0; i < this.scene.children.length; i++) {
        if (this.scene.children[i].type === "Mesh") {
          count += 1;
        }
      }
      return count;
    },
    addFireworks: function(intersects, objectSize, totalObjects, scene, dirs) {
      const expPosX = intersects[0].object.position.x;
      const expPosY = intersects[0].object.position.y;
      const expColor = intersects[0].object.material.color.getHex();
      let particles =  new ExplodeAnimation(expPosX, expPosY, expColor, objectSize, totalObjects, scene, dirs);
      particles.createPartices();
      this.parts.push(
       particles
      );
    },
    getIntersects: function(event) {
      let mouse = new THREE.Vector2();
      mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
      mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;
      let raycaster = new THREE.Raycaster();
      raycaster.setFromCamera(mouse, this.camera);
      let intersects = raycaster.intersectObjects(this.scene.children);
      return intersects;
    },
    mouseMoveSetColor: function(objectMaterial) {
      let randomColorIndex = Math.floor(Math.random() * this.colorArray.length);
      let colorMaterial = this.colorArray[randomColorIndex];
      if (objectMaterial.color.getHex() == 0xffffff) {
        objectMaterial.color.setHex(colorMaterial);
        objectMaterial.opacity = 1;
      }
    },
    scaleAnimation: function(object, factor, time) {
      new TWEEN.Tween(object.scale)
        .to(
          {
            x: factor,
            y: factor,
            z: factor
          },
          time
        )
        .easing(TWEEN.Easing.Elastic.Out)
        .start();
    },
    animate: function() {
      requestAnimationFrame(this.animate);
      this.renderer.render(this.scene, this.camera);
      TWEEN.update();
      let pCount = this.parts.length;
      while (pCount--) {
        this.parts[pCount].update();
      }
    }
  },
  mounted() {
    this.init();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.page-logo {
  width: 70%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
#container {
  position: absolute;
  top: 0;
  left: 0;
}
.pointsDisplay {
  position: absolute;
  z-index: 1000;
  color: #000;
  font-size: 30px;
  padding: 35px 70px;
  font-family: "Poppins", sans-serif;
  font-weight: 800;
  transform: scale(0);
  background: url("../assets/bubbles/assets/points-background1.png") no-repeat
    top left;
  background-size: cover;
  animation: none;
}
</style>
