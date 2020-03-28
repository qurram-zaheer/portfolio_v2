<template>
  <div
    :style="{backgroundColor: currentTheme[0], color: currentTheme[1]}"
    class="main unselectable"
    v-on:scroll="back = !back"
  >
    <Header />
    <div class="links">
      <p class="button--green" @click="randomize">Switch theme</p>
    </div>
    <div class="container">
      <div class="inner">
        <h1 class="title">Hi, I'm Qurram!</h1>
        <h2
          class="subtitle"
          style="font-weight: 200"
        >Programming enthusiast | Aspiring Full-Stack dev | Geek</h2>
        <div style="display: flex; flex-direction: row; justify-content: center">
          <div v-for="item in social" :key="item.link">
            <a :href="item.link">
              <Thumbnail
                :url="'https://img.icons8.com/windows/48/000000/' + item.img"
                class="social"
              />
            </a>
          </div>
        </div>
      </div>
    </div>
    <div id="about" class="about">
      <div>
        <div class="about-card">
          <h2 class="subtitle">About me</h2>
          <p class="para">I love programming!</p>
          <p class="para">
            My love of code first started with webdev, and I still enjoy trying to make every website make have pixel perfect UI, responsiveness and intuitive functionality.
            I've played around with a bunch of web frameworks/libraries: React, Vue.js (my favorite!) and django, alongwith Node and Express.
          </p>
          <p class="para">
            Recently, I've been trying to get into Rust, which I've found very fun to work with.
            I love reading! I also love public speaking and trying to keep an audience engaged.
          </p>
          <div class="tech para">
            <p class="subtitle2">Stuff I'm familiar with:</p>
            <div style="display: flex; flex-wrap: wrap; max-width: 300px; padding: 5px">
              <div v-for="item in technologies" :key="item" class="item">
                <b>></b>
                {{item}}
              </div>
            </div>
            <p
              style="max-width: 100%; text-align: center; font-size: 3.5rem; padding-bottom: 10px"
            >\ (•◡•) /</p>
          </div>
        </div>
      </div>
    </div>
    <div class="projects" id="projects">
      <div class="project-container">
        <h2 class="subtitle">Stuff I've made</h2>
        <div class="project-deck">
          <Project v-for="project in projects" :key="project" :project="project" />
        </div>
        <hr />Check out my Github for more!
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Project from "@/components/Project.vue";
import Thumbnail from "@/components/Thumbnail.vue";
import Footer from "@/components/Footer.vue";

export default {
  layout: "default",
  components: { Header, Project, Thumbnail, Footer },
  data() {
    return {
      colorList: [
        ["#fafafa", "#4ea9da"],
        ["#fafafa", "#3dc0b0"],
        ["#fafafa", "#485564"],
        ["#fafafa", "#89303d"],
        ["#fafafa", "#2b5c50"]
      ],
      social: [
        { img: "github.png", link: "https://github.com/qurram-zaheer" },
        {
          img: "linkedin.png",
          link: "https://www.linkedin.com/in/qurram-zaheer-aa08051a0/"
        },
        { img: "twitter.png", link: "https://twitter.com/Decoherence17" }
      ],
      currentTheme: ["#fafafa", "#89303d"],
      technologies: ["Python", "JS (ES6+)", "Node.js", "Rust", "C#"],
      hoverStatus: false,
      projects: [
        {
          name: "qFeedbacker",
          desc: "Batch email sender, with OAuth; powered by Stripe",
          tech: [
            "javascript.png",
            "mongodb.png",
            "react-native.png",
            "npm.png",
            "redux.png"
          ],
          url: "https://github.com/qurram-zaheer/qfeedbacker"
        },
        {
          name: "JSRec",
          desc: "Face recognition webapp, powered by Clarifai",
          tech: [
            "javascript.png",
            "react-native.png",
            "npm.png",
            "postgreesql.png"
          ],
          url: "https://github.com/qurram-zaheer/jsrec-frontend"
        },
        {
          name: "qDex",
          desc: "Custom fully functional pokedex",
          tech: ["javascript.png", "react-native.png"],
          url: "https://github.com/qurram-zaheer/qurram_dex"
        },
        {
          name: "Dummy blog",
          desc: "Dummy blog made with SSR Vue, powered by Nuxt",
          tech: ["javascript.png", "vue-js"],
          url: "https://github.com/qurram-zaheer/dummy-blog"
        }
      ]
    };
  },
  methods: {
    randomize() {
      let order = Math.floor(Math.random() * Math.floor(2));
      let index = Math.floor(Math.random() * Math.floor(this.colorList.length));
      if (order === 0) {
        this.currentTheme = this.colorList[index];
      } else {
        this.currentTheme = this.colorList[index].reverse();
      }
    }
  }
};
</script>

<style>
html {
  scroll-behavior: smooth;
}

.unselectable {
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;

  /*
     Introduced in Internet Explorer 10.
     See http://ie.microsoft.com/testdrive/HTML5/msUserSelect/
   */
  -ms-user-select: none;
  user-select: none;
}
.social {
  -webkit-transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
  transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
}
.social::after {
  z-index: -1;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  opacity: 0;
  -webkit-transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
  transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
}

.social:hover {
  -webkit-transform: scale(1.25, 1.25);
  transform: scale(1.25, 1.25);
}

.social:hover::after {
  opacity: 1;
}

.img-row {
  display: flex;
  flex-wrap: wrap;
}
.project-deck {
  display: flex;
  flex-wrap: wrap;
  padding-bottom: 3px;
}
.projects {
  max-width: 1200px;
  min-height: 95vh;
  margin: 0 auto;
  text-align: left;
}

.container2 {
  display: flex;
  flex-wrap: wrap;
}

.main {
  background-image: radial-gradient(#212121 3%, transparent 3%),
    radial-gradient(#fafafa 3%, transparent 3%);
  background-position: 0 0, 50px 50px;
  background-size: 100px 100px;
  min-width: 100vw;
}

.inner {
  margin: 30px;
}
.container {
  margin: 0 auto;
  min-height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 6rem;
  letter-spacing: 1px;
  font-weight: 600;
}

.subtitle {
  font-weight: 400;
  font-size: 1.8rem;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding: 12px;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 3;
}

.about {
  text-align: left;
  padding: 2rem;
  max-width: 1200px;
  min-height: 95vh;
  display: flex;
  margin: 0 auto;
}

.para {
  font-size: 1.1rem;
  line-height: 2rem;
  padding-top: 0.8rem;
}

.item {
  padding: 5px;
  min-width: 50%;
}
.subtitle2 {
  font-weight: 500;
}

.about-card {
  background-color: rgba(250, 250, 250, 0.1);
  border-radius: 12px;
  border: 1px solid black;
  padding: 40px;
}

.project-container {
  background-color: rgba(250, 250, 250, 0.1);
  border-radius: 12px;
  border: 1px solid black;
  padding: 40px;
}

@supports (-webkit-backdrop-filter: none) or (backdrop-filter: none) {
  .about-card {
    -webkit-backdrop-filter: blur(2px);
    backdrop-filter: blur(2px);
    background-color: rgba(255, 255, 255, 0.1);
  }
  .project-container {
    -webkit-backdrop-filter: blur(2px);
    backdrop-filter: blur(2px);
    background-color: rgba(255, 255, 255, 0.1);
  }
}
</style>
