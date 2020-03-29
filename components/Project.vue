<template>
  <div class="projects-card box">
    <div class="container2">
      <div class="card">
        <div class="content">
          <h2 class="subtitle">{{project.name}}</h2>
          <p class="desc">{{project.desc}}</p>
        </div>
        <hr style="height: 3px" />
        <div class="image-row">
          <div class="thumb" v-for="tech in project.tech" :key="tech">
            <app-thumbnail :url="'https://img.icons8.com/color/36/000000/' + tech"></app-thumbnail>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Thumbnail from "@/components/Thumbnail.vue";

export default {
  props: ["project"],
  components: {
    AppThumbnail: Thumbnail
  },
  methods: {
    openGit() {
      location.replace(this.project.url);
    }
  }
};
</script>

<style>
.image-row {
  display: flex;
  flex-wrap: wrap;
  margin-top: 10px;
}
.projects-card {
  padding: 2rem;
  max-width: 300px;
  min-width: 300px;
  border: 1px solid black;
  margin: 5px;
}
@media (max-width: 600px) {
  .projects-card {
    min-width: 100%;
  }
  .about {
    padding: 0px !important;
    padding-bottom: 5px !important;
  }
  .container {
    padding-bottom: 5px;
  }
  .title {
    font-size: 4rem !important;
  }
  .subtitle {
    font-size: 1.2rem !important;
  }
  .para {
    font-size: 0.975rem !important;
  }
  .navbar {
    font-size: 0.8rem;
  }
  .button--green {
    padding: 5px 10px;
  }
}

.content {
  max-height: 180px;
  min-height: 120px;
}
.thumb {
  padding-right: 5px;
}

.box {
  border-radius: 5px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.7);
  -webkit-transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
  transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
}

.box::after {
  border-radius: 5px;
  z-index: -1;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.9);
  opacity: 0;
  -webkit-transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
  transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
}

.box:hover {
  -webkit-transform: scale(1.03, 1.03);
  transform: scale(1.03, 1.03);
}

.box:hover::after {
  opacity: 1;
}
</style>