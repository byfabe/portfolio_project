<template>
  <div class="home">
    <div class="container-window">
      <ul class="circles">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <div class="window">
        <div class="window-left">
          <div class="window-wrapper">
            <div class="presentation">
              <div class="presentation-front">
                <div class="container-name">
                  <p class="name">Fabien</p>
                  <p class="name">Rivet</p>
                  <img
                    src="../assets/portfolio.png"
                    alt=""
                    class="portfolio-icon"
                  />
                </div>
                <div class="container-portfolio">
                  <span class="portfolio">Développeur web</span>
                </div>
              </div>

              <div class="presentation-back">
                <Popper content="CV" hover="true" placement="right">
                  <a
                    href="https://www.rivetportfolio.ovh/CV_Fabien_Rivet.pdf"
                    download="CV_Fabien_Rivet.pdf"
                    ><img src="../assets/cv2.png" alt="" class="icon" /></a
                ></Popper>
                <Popper content="GitHub" hover="true" placement="right">
                  <a
                    href="https://github.com/byfabe?tab=repositories"
                    target="_blank"
                    ><img src="../assets/github.png" alt="" class="icon" /></a
                ></Popper>
                <Popper content="Email" hover="true" placement="right">
                  <a href="mailto:byfabe@gmail.com" target="_blank"
                    ><img src="../assets/email.png" alt="" class="icon" /></a
                ></Popper>
              </div>
            </div>
          </div>
        </div>
        <div class="card-container" @mouseover="play()" @mouseleave="pause()">
          <div class="card-wrapper" v-for="project in projects" :key="project">
            <div class="card">
              <div class="card-front">
                <h2>{{ project.title }}</h2>
                <p v-html="project.description"></p>
                <p :class="project.class" v-html="project.description2"></p>
              </div>
              <div class="card-back">
                <a :href="project.link" target="_blank">
                  <img
                    :src="require(`@/assets/${project.source}`)"
                    alt=""
                    v-if="project.source.includes('jpg')"
                  />
                  <video
                    loop="true"
                    muted="true"
                    v-if="project.source.includes('mp4')"
                  >
                    <source
                      :src="require(`@/assets/${project.source}`)"
                      type="video/mp4"
                    />
                  </video>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Popper from "vue3-popper";
export default {
  components: {
    Popper,
  },
  data() {
    return {
      projects: [
        {
          title: "Marvalak",
          description: "Histoire interactive avec Vue.js. (démo)",
          link: "https://marvalak.netlify.app/",
          source: "marvalak.jpg",
        },
        {
          title: "Symbiosis",
          description:
            "Site web personnel (version développement) entièrement éditable.",
            description2:  "user: admin // password: admin",
          link: "https://symbiosisproject.netlify.app/",
          source: "symbiosis.mp4",
          class: "description"
        },
        {
          title: "youmee.",
          description: "Chat avec socket.io, node.js et vue.js.",
          link: "https://youmee.netlify.app/",
          source: "youmee.mp4",
        },
        {
          title: "Memento",
          description: "Post-it animés avec Vue.js et greensock.",
          link: "http://memento.cool/",
          source: "memento.mp4",
        },
        {
          title: "Honfleur",
          description: "Site vitrine avec slideshow draggable.",
          link: "https://objective-poincare-859034.netlify.app/",
          source: "honfleur.mp4",
        },
      ],
    };
  },
  methods: {
    play() {
      let video = document.querySelectorAll("video");
      for (let i = 0; i < video.length; i++) {
        video[i].play();
      }
    },
    pause() {
      let video = document.querySelectorAll("video");
      for (let i = 0; i < video.length; i++) {
        video[i].pause();
      }
    },
  },
};
</script>

<style lang="scss">
.container-window {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #f2a679;
  z-index: -2;
  & .window {
    display: flex;
    width: 80%;
    height: 70%;
    & .window-left {
      width: 50%;
      height: 100%;
      mix-blend-mode: darken;
      margin-right: 5%;
      & .window-wrapper {
        position: relative;
        height: 100%;
        min-height: 50%;
        perspective: 2000px;
        perspective-origin: top;
      }
      & .window-wrapper:hover .presentation {
        transform: rotateY(180deg);
      }
      & .presentation {
        position: relative;
        height: 100%;
        transform-style: preserve-3d;
        transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
      }
      & .presentation-front,
      .presentation-back {
        position: absolute;
        height: 100%;
        width: 100%;
        box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px,
          rgb(51, 51, 51) 0px 0px 0px 3px;
        backface-visibility: hidden;
        -webkit-backface-visibility: hidden;
      }
      & .presentation-front {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        background: #f25252;
      }
      & .presentation-back {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        background: #f25252;
        transform: rotateY(180deg);
        & .popper {
          background: #f2a679;
          border: 2px solid rgba(0, 0, 0, 0.753);
          border-radius: 5px;
          padding: 2%;
          color: rgb(37, 37, 37);
          font-family: "Righteous", cursive;
          font-size: 1vw;
          transition: opacity 0.7s cubic-bezier(0.86, 0, 0.07, 1);
        }
        & .icon {
          width: 10vw;
          transition: all 0.5s cubic-bezier(0.86, 0, 0.07, 1);
          &:hover {
            transform: scale(1.2);
            transition: all 0.5s cubic-bezier(0.86, 0, 0.07, 1);
          }
        }
      }
      & .container-name {
        position: relative;
        text-align: center;
        padding: 3%;
        border: 5px solid #f2a679;
      }
      & .portfolio-icon {
        width: 55%;
      }
      & .portfolio-icon {
        position: absolute;
        bottom: -48%;
        right: -40%;
        transform: rotate(-20deg);
      }
      & p,
      span {
        font-family: "Righteous", cursive;
        font-size: 2.5vw;
        color: #f2a679;
        user-select: none;
      }
    }
  }
}
.card-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 30px;
  width: 60%;
  padding: 3px;
  overflow-y: scroll;
  & .card-wrapper {
    position: relative;
    height: 30vh;
    min-height: 50%;
    perspective: 2000px;
    perspective-origin: top;
  }
  & .card-wrapper:hover .card {
    transform: rotateY(180deg);
  }
  & .card {
    position: relative;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
  }
  & .card-front,
  .card-back {
    position: absolute;
    height: 100%;
    width: 100%;
    backface-visibility: hidden;
    -webkit-backface-visibility: hidden;
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px, rgb(51, 51, 51) 0px 0px 0px 3px;
  }
  & .card-front {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background: #3a8c75;
    & h2 {
      text-align: center;
      font-family: "Righteous", cursive;
      font-size: 2.5vw;
      color: #f2a679;
      margin-bottom: 2%;
    }
    & .description {
      font-weight: bold;
    }
    & .oc-title {
      font-size: clamp(25px, 2vw, 50px);
      text-align: center;
    }
    & p {
      font-family: "Raleway", cursive;
      font-size: 1vw;
      font-weight: 500;
      color: rgb(37, 37, 37);
      width: 80%;
      text-align: center;
    }
  }
  & .card-back {
    transform: rotateY(180deg);
    background: #3a8c75;
    & img {
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
    & video {
      width: 100%;
      height: 100%;
      //object-fit: cover;
    }
  }
}
@keyframes animate {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 1;
    border-radius: 0;
  }

  100% {
    transform: translateY(-1500px) rotate(720deg);
    opacity: 0;
    border-radius: 30%;
  }
}
.circles {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.circles li {
  position: absolute;
  display: block;
  list-style: none;
  width: 20px;
  height: 20px;
  background: #f25252;
  animation: animate 25s linear infinite;
  bottom: -150px;
}

.circles li:nth-child(1) {
  left: 25%;
  width: 80px;
  height: 80px;
  animation-delay: 0s;
  background: #3a8c75;
}

.circles li:nth-child(2) {
  left: 10%;
  width: 20px;
  height: 20px;
  animation-delay: 2s;
  animation-duration: 12s;
  background: #3a8c75;
}

.circles li:nth-child(3) {
  left: 70%;
  width: 20px;
  height: 20px;
  animation-delay: 4s;
}

.circles li:nth-child(4) {
  left: 40%;
  width: 60px;
  height: 60px;
  animation-delay: 0s;
  animation-duration: 18s;
  background: #3a8c75;
}

.circles li:nth-child(5) {
  left: 65%;
  width: 20px;
  height: 20px;
  animation-delay: 0s;
}

.circles li:nth-child(6) {
  left: 75%;
  width: 110px;
  height: 110px;
  animation-delay: 3s;
}

.circles li:nth-child(7) {
  left: 35%;
  width: 100px;
  height: 100px;
  animation-delay: 7s;
  background: #3a8c75;
}

.circles li:nth-child(8) {
  left: 50%;
  width: 25px;
  height: 25px;
  animation-delay: 15s;
  animation-duration: 45s;
}

.circles li:nth-child(9) {
  left: 20%;
  width: 15px;
  height: 15px;
  animation-delay: 2s;
  animation-duration: 35s;
  background: #3a8c75;
}

.circles li:nth-child(10) {
  left: 85%;
  width: 100px;
  height: 100px;
  animation-delay: 0s;
  animation-duration: 11s;
}
@media screen and (max-width: 1440px) {
  .container-window {
    & .window {
      justify-content: center;
      align-items: center;
      flex-direction: column;
      width: 100%;
      height: 100%;
      overflow: auto;
      & .window-left {
        width: 60%;
        margin: 30px 0 30px 0;
        & p,
        span {
          font-size: clamp(28px, 2.8vw, 50px);
        }
        & .presentation-back {
          display: flex;
          flex-direction: row;
        }
      }
    }
  }

  .card-container {
    display: flex;
    flex-direction: column;
    width: 60%;
    height: 100%;
  }
  .card {
    & .card-front {
      & h2 {
        font-size: clamp(30px, 2.8vw, 50px);
      }
      & p {
        font-size: clamp(16px, 1.6vw, 20px);
      }
    }
  }
}
@media screen and (max-width: 768px) {
  .container-window {
    & .window {
      & .window-left {
        width: 80%;
      }
    }
  }
  .card-container {
    width: 80%;
  }
}
@media screen and (max-width: 425px) {
  .container-window {
    & .window {
      & .window-left {
        & .presentation-back {
          display: flex;
          flex-direction: column;
        }
      }
    }
  }
  :deep(.popper) {
    border: 1px solid rgba(0, 0, 0, 0.753);
    font-size: 1.2vw;
  }
}
</style>