<template>
  <div class="contenitore">
    <div class="container">
      <h1 v-if="(arrFilm.length)">
        Movies
      </h1>
      <div
        class="Card"
      >
        <div
          v-for="obj in arrFilm"
          :key="obj.id"
          class="info"
        >
          <div class="flip">
            <div class="titolo">
              {{ obj.original_title }}
            </div>
            <div>
              Lingua:
              <lang-flag
                class="bandiera"
                :iso="obj.original_language"
              />
            </div>

            <div>{{ `voto: ${obj.vote_average} / 10` }}</div>
            <div>
              {{ obj.overview }}
            </div>
          </div>
          <div class="card-front">
            <img
              :src="`https://image.tmdb.org/t/p/w500${obj.poster_path}`"
              alt=""
            >
          </div>
          <div>{{ obj.title }}</div>
        </div>
      </div>
      <h1
        v-if="(arrSerie.length)"
      >
        Series Tv
      </h1>
      <div
        class="Card"
      >
        <div
          v-for="obj in arrSerie"
          :key="obj.id"
          class="info"
        >
          <div class="flip">
            <div class="titolo">
              {{ obj.original_name }}
            </div>
            <div>
              Lingua:
              <lang-flag
                class="bandiera"
                :iso="obj.original_language"
              />
            </div>
            <div>{{ `voto: ${obj.vote_average} / 10` }}</div>
            <div>
              {{ obj.overview }}
            </div>
          </div>
          <div class="card-front">
            <img
              :src="`https://image.tmdb.org/t/p/w342${obj.poster_path}`"
              alt=""
            >
          </div>
          <div>{{ obj.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  components: {
    LangFlag,
  },
  props: {
    arrFilm: Array,
    arrSerie: Array,
  },

};
</script>

  <style lang="scss" scoped>
    .contenitore{
      min-height: 100vh;
      background-color: #313131;
    }

    .container{
      color: red;
      font-size:20px ;
    }

    ul{
      list-style: none;
    }

    img{
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .Card{
      display: flex;
      justify-content: space-around;
      align-content: center;
      gap:15px;
      padding-top: 20px;
      color: white;
      flex-wrap: wrap;
    }

    h1{
      padding-top: 80px;
    }

    .bandiera, .titolo{
      font-size:20px;
      font-weight: 700;
      margin-bottom: 10px;
    }

    .info{
      position: relative;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-direction: column;
      margin-bottom: 90px;
      height: 350px;
      width: 250px;
    }

    .flip{
      position: absolute;
      padding:10px;
      width: 100%;
      height: 100%;
      margin: auto;
      color: white;
      font-size: 13px;
      font-weight: 300;
      display: none;
    }

    .card-front{
      width: 100%;
      height: 100%;
      margin: auto;
      text-align: center;
      opacity: 1;

    }
    .card-front:hover{
      opacity: 0;
    }

    .info:hover .flip {
      display: block;
      background-color: black;
    }

  </style>
