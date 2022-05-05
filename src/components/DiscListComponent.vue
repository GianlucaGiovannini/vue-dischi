<template>
  <section v-if="!loading">
    <div class="container">
      <div
        class="row row-cols-1 row-cols-md-2 row-cols-lg-3 row-cols-xl-4 row-cols-xxl-5">
        <DiscItem :album="album" v-for="(album, index) in discs" :key="index" />
      </div>
    </div>
  </section>
  <section v-else class="d-flex align-items-center justify-content-center min-vh-100">
    <Loader />
  </section>
</template>

<script>
import axios from "axios";
import DiscItem from "@/components/DiscItemComponent.vue";
import Loader from "@/components/LoaderComponent.vue";

export default {
  name: "DiscListComponent",
  components: {
    DiscItem,
    Loader,
  },
  data() {
    return {
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      discs: null,
      loading: true,
      error: null,
    };
  },
  methods: {
    timer() {
      setTimeout(() => {
        this.loading = false
      }, 2500);
    },

    callApi() {
      axios
        .get(this.API_URL)
        .then((response) => {
          this.discs = response.data.response;
          /* this.loading = false; */
        })
        .catch((error) => {
          console.error(error);
          /* this.error = `Sorry There is a Problem! ${error}`; */
        });
    },
  },
  mounted() {
    this.callApi();
    this.timer();
  },
};
</script>

<style lang="scss" scoped>

</style>