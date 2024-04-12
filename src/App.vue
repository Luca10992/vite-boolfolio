<script>
import axios from "axios";
import { store } from "./store";

export default {
  data() {
    return {
      store,
    };
  },

  created() {
    axios.get(store.api.baseUrl + "projects").then((res) => {
      store.projects = res.data.data;
    });
  },
};
</script>

<template>
  <div class="container py-5">
    <div class="row g-3">
      <div v-for="project in store.projects" class="col-3">
        <div class="card h-100">
          <img
            class="card-img-top"
            :src="
              project.thumb
                ? project.thumb
                : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTIU04WE68MpK7kIJ_kHfCEY5NFXNegUYUJ8-pFSM7uEg&s'
            "
            alt=""
          />
          <div class="card-body">
            <h5>{{ project.title }}</h5>
            <span v-for="technology in project.technologies">
              - {{ technology.label }}
            </span>
            <div class="text-end">
              <div
                class="badge"
                :style="'background-color:' + project.type.color"
              >
                <p class="m-0">{{ project.type.label }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@use "./src/style/general.scss";
</style>
