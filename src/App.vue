<template>
  <div id="app">
    <div class="navbar">
      <img
        style="align-items: flex-start;margin-top: auto;margin-bottom: auto;padding-left: 5px;"
        src="./assets/logo.webp"
        height="50"
      />
    </div>
    <div class="pages page1">
      <div class="landing">
        <div class="neon-me glow" id="person">
          <img svg-inline src="./assets/Neon Me.svg" />
        </div>
        <div></div>
        <div class="name glow" id="name">
          <img svg-inline style="margin: auto;" class="name" src="./assets/name.svg" />
        </div>

        <div></div>
        <div style="outline: none;" id="project-button">
          <img class="project-button glow" svg-inline src="./assets/NeonCard.svg" />
        </div>
      </div>
    </div>

    <div class="pages page2"></div>
    <div class="pages page3"></div>
    <div class="pages page4"></div>
  </div>
</template>

<script>
import anime from "animejs/lib/anime.min.js";

export default {
  name: "app",
  components: {},
  mounted() {
    this.$nextTick(() => {
      // container IS finished rendering to the DOM

      const neonArray = [
        {
          element: document.getElementById("person").querySelectorAll("path"),
          duration: 5000,
          delay: 200
        },
        {
          element: document.getElementById("name").querySelectorAll("path"),
          duration: 10000,
          delay: 200
        },
        {
          element: document
            .getElementById("project-button")
            .querySelectorAll("path"),
          duration: 8000,
          delay: 200
        }
      ];

      function animateLines(elementArray) {
        elementArray.forEach(element => {
          for (var i = 0; i < element.element.length; i++) {
            var pathEl = element.element[i];

            var offset = anime.setDashoffset(pathEl);
            pathEl.setAttribute("stroke-dashoffset", offset);
            anime({
              targets: pathEl,
              strokeDashoffset: [offset, 0],
              duration: element.duration,
              delay: element.delay,
              loop: false,
              direction: "alternate",
              easing: "easeInOutSine",
              autoplay: true
            });
          }
        });
      }

      animateLines(neonArray);
    });
  }
};
</script>

<style lang="scss">
.navbar {
  z-index: 1;
  position: fixed;
  display: flex;
  top: 0px;
  width: 100vw;
  height: 60px;
  backdrop-filter: blur(10px);
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
  z-index: 0;
  // background-color: red;
}

.neon-me {
  position: absolute;
  bottom: 0px;
  width: 30vw;
  outline: none;
  pointer-events: none;
}

.project-button {
  display: grid;
  margin: auto;
  outline: none;
}

.project-button:hover {
  filter: drop-shadow(0px 0px 2px #82fae600);
}
.project-button:active {
  filter: drop-shadow(0px 0px 2px #09fbd3) drop-shadow(0px 0px 10px #09fbd318)
    drop-shadow(0px 0px 15px #09fbd300);
}

.name {
  display: grid;
  margin: auto;
  width: 90%;
  pointer-events: none;
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

@media only screen and (min-height: 1200px) {
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
