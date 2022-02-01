<template>
  <div id="app">
    <header-content />
    <select-bar @selectGenre="filterGenresResult"
      @selectAuthor="filterArtistResult"
      :genres="genresFiltered"
      :artists="artistFiltered"
    />
    <main-container v-if="apiLoad" :discs="discFiltered" />
    <loader-content v-else />
  </div>
</template>

<script>
import axios from "axios";
import HeaderContent from "./components/HeaderContent.vue";
import MainContainer from "./components/MainContainer.vue";
import LoaderContent from "./components/LoaderContent.vue";
import SelectBar from "./components/SelectBar.vue";

export default {
  name: "App",
  components: {
    HeaderContent,
    MainContainer,
    LoaderContent,
    SelectBar,
  },
  data() {
    return {
      discs: [],
      discFiltered: [],
      genresFiltered: [],
      artistFiltered: [],
      apiLoad: false,
    };
  },
  methods: {
    filterGenresResult(select) {
      this.discFiltered = this.discs.filter((disk) => {
        return disk.genre.includes(select);
      });
    },
    filterArtistResult(select) {
      this.discFiltered = this.discs.filter((disk) => {
        return disk.author.includes(select);
      });
    }
  },
  mounted() {
    setTimeout(() => {
      axios("https://flynn.boolean.careers/exercises/api/array/music").then(
        (result) => {
          this.discs = result.data.response;
          this.discFiltered = this.discs;
          this.apiLoad = true;

          //GENRES

          this.discs.forEach((e) => {
            if (!this.genresFiltered.includes(e.genre)) {
              this.genresFiltered.push(e.genre);
            }
          });

          //AUTHOR

          this.discs.forEach((e) => {
            if (!this.artistFiltered.includes(e.author)) {
              this.artistFiltered.push(e.author);
            }
          });
        }
      );
    }, 2000);
  },
};
</script>

<style lang="scss">
@import "@/style/main.scss";
</style>