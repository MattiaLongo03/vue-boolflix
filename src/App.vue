<template>
  <div>
    <HeaderPage @searchedValue="filmName" />
    <MainPage
      :arr-film="arrFilm"
      :arr-serie="arrSerie"
    />
  </div>
</template>

<script>
import HeaderPage from '@/components/HeaderPage.vue';
import MainPage from '@/components/MainPage.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },

  data() {
    return {
      baseApiUrl: 'https://api.themoviedb.org/3',
      apikey: '3e31986dee38cb6841668a9b421f4f5f',
      resultsLanguage: 'it-IT',
      arrFilm: [],
      arrSerie: [],
    };
  },

  methods: {
    filmName(value) {
      axios.get(`${this.baseApiUrl}/search/movie`, {
        params: {
          api_key: this.apikey,
          query: value,
          language: this.resultsLanguage,
        },
      })
        .then((responseAxios) => {
          this.arrFilm = responseAxios.data.results.slice(0, 8);
        });

      axios.get(`${this.baseApiUrl}/search/tv`, {
        params: {
          api_key: this.apikey,
          query: value,
          language: this.resultsLanguage,
        },
      })
        .then((responseAxios) => {
          this.arrSerie = responseAxios.data.results.slice(0, 8);
        });
    },
  },

};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>
