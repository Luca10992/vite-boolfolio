<script>
import axios from "axios";
import { store } from "../store";
import AppCard from "./AppCard.vue";

export default {
  data() {
    return {
      store,
      pagination: [],
    };
  },
  components: { AppCard },

  methods: {
    fetchProject(endPoint = store.api.baseUrl + "projects") {
      axios.get(endPoint).then((res) => {
        store.projects = res.data.data;
        this.pagination = res.data.links;
      });
    },
  },

  created() {
    this.fetchProject();
  },
};
</script>

<template>
  <div class="row row-cols-4 g-3 mb-2">
    <!-- <app-card v-for="project in store.projects" :project="project"></app-card> -->
    <div class="col" v-for="project in store.projects">
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
  <nav aria-label="Page navigation">
    <ul class="pagination">
      <li
        @click="fetchProject(link.url)"
        :class="{ active: link.active, disabled: !link.url }"
        v-for="link in pagination"
        class="page-item"
      >
        <a class="page-link" href="#" v-html="link.label"></a>
      </li>
    </ul>
  </nav>
</template>

<style lang="scss">
@use "./src/style/general.scss";
</style>
