<script>
import axios from "axios";
import { store } from "../store";

export default {
  data() {
    return {
      store,
      project: null,
    };
  },
  created() {
    const projectId = this.$route.params.id;
    axios.get(store.api.baseUrl + `projects/${projectId}`).then((res) => {
      this.project = res.data;
    });
  },
};
</script>

<template>
  <h1 class="fw-bold fs-2">{{ this.project.title }}</h1>
  <div class="show-container d-flex gap-3">
    <div class="w-50">
      <img
        class="card-img-top"
        :src="
          this.project.thumb
            ? this.project.thumb
            : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTIU04WE68MpK7kIJ_kHfCEY5NFXNegUYUJ8-pFSM7uEg&s'
        "
        alt="img-detail"
      />
    </div>
    <div class="w-50 d-flex flex-column justify-content-between">
      <div>
        <h5>
          <strong> Descrizione: </strong>
          <p class="d-inline">{{ this.project.description }}</p>
        </h5>
        <div>
          <h5 class="m-0 fw-bold">Tecnologie:</h5>
          <span v-for="technology in this.project.technologies">
            ●{{ technology.label }}
          </span>
        </div>
      </div>
      <div class="d-flex justify-content-between align-items-center">
        <div
          class="badge fs-6 p-1 my-2"
          :style="'background-color:' + this.project.type.color"
        >
          {{ this.project.type.label }}
        </div>
        <a href="https://github.com/Luca10992?tab=repositories" target="blank">
          <button class="btn btn-secondary">Vai al progetto</button>
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@use "./src/style/general.scss";
</style>
