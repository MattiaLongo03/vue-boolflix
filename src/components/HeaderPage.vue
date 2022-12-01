<template>
  <div class="navbar">
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('searchedValue', filmStr)">
      <label for="film">
        <input
          id="searchMovie"
          v-model="filmStr"
          type="text"
          name="searchMovie"
          placeholder="Inserisci Titolo"
        >
      </label>
      <button>
        Cerca
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'HeaderPage',
  data() {
    return {
      filmStr: '',
    };
  },
};

</script>

<style scoped lang="scss">
    .navbar{
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 100px;
    background-color: black;
    color: red;
  }
</style>
