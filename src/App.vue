<template>
  <div>
    <HeaderPage />
    <MainPage />
  </div>
</template>

<script>
import HeaderPage from '@/components/HeaderPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>
