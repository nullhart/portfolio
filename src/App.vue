<template>
  <div id="app">
    <div class="navbar">
      <img
        style="  margin-top: auto;margin-bottom: auto;margin-left: 5px;"
        src="./assets/logo.png"
        height="50"
      />
    </div>
    <div class="pages page1">
      <div class="landing">
        <img svg-inline class="neon-me glow" id="neon-me" src="./assets/Neon Me.svg" />

        <div></div>

        <img svg-inline class="name glow" id="name" style="margin: auto;" src="./assets/name.svg" />

        <div></div>

        <img svg-inline class="project-button glow" id="project-button" src="./assets/NeonCard.svg" />
      </div>
    </div>

    <div class="pages page2"></div>
    <div class="pages page3"></div>
    <div class="pages page4"></div>
  </div>
</template>

<script>
import anime from "animejs/lib/anime.es.js";

export default {
  name: "app",
  components: {},
  mounted() {
    var neonMe = document.querySelectorAll("path");

    for (var i = 0; i < neonMe.length; i++) {
      var pathEl = neonMe[i];

      var offset = anime.setDashoffset(pathEl);
      pathEl.setAttribute("stroke-dashoffset", offset);
      anime({
        targets: pathEl,
        strokeDashoffset: [offset, 0],
        duration: 3000,
        delay: 200,
        loop: false,
        direction: "alternate",
        easing: "easeInOutSine",
        autoplay: true
      });
    }
  }
};
</script>

<style lang="scss">
.app {
  display: grid;
  grid-template-rows: repeat(4, 100vh);
}

.navbar {
  position: fixed;
  display: flex;
  top: 0px;
  width: 100vw;
  height: 60px;
  backdrop-filter: blur(10px);
  z-index: 1;
  background: rgba(196, 196, 196, 0.2);
}

.pages {
  display: grid;
  height: 100vh;
  color: white;
}

.glow {
  filter: drop-shadow(0px 0px 2px #09fbd3) drop-shadow(0px 0px 10px #09fbd388)
    drop-shadow(0px 0px 15px #09fbd356);
}
.page1 {
  background-color: rgb(0, 0, 0);
}
.page2 {
  background: linear-gradient(to bottom, #000000, #0f2027);
}
.page3 {
  background-color: #0f2027;
}
.page4 {
  background-color: #0f2027;
}
svg {
  background-color: transparent;
}

.landing {
  display: grid;
  grid-template-columns: 30vw 1fr;
  height: 100vh;
  grid-template-rows: 60fr 40fr;
  // background-color: red;
}

.neon-me {
  position: absolute;
  bottom: 0px;
  width: 30vw;
}

.project-button {
  display: grid;
  margin: auto;
}

.project-button:hover {
  filter: drop-shadow(0 0 30px #09fbd3);
}
.project-button:active {
  filter: drop-shadow(0 0 10px #09fbd3);
}

.name {
  display: grid;
  margin: auto;
  width: 100%;

  stroke-dasharray: 200px;
}

// Mobile
@media only screen and (max-width: 700px) {
  .landing {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 0fr 1fr 0fr 1fr;
    height: 100vh;
    margin: auto;
    // background-color: red;
  }
  .name {
    width: 90vw;
  }
  .neon-me {
    position: absolute;
    bottom: 0vh;
    left: 0px;
    width: 40vh;
  }
  .project-button {
    position: absolute;
    right: 5px;
    bottom: 30vh;
    width: 40vw;
    height: auto;
  }
}
</style>
