<template>
  <div>
    <Layout >
      <NuxtPage class="layout"/>
    </Layout>
  </div>
</template>

<script lang="ts" setup>
import Layout from "./layouts/Layout.vue"

</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700;800;900&display=swap');

html {
  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  background-image: url("./assets/background_mobile.png");
  background-size: cover;
  background-repeat: no-repeat;
  scroll-behavior: smooth;

  @media screen and (min-width: 768px) {
    background-position: center;
    background-image: url("./assets/background.png");
    background-size: cover;
  background-repeat: no-repeat;
  }
  
  h1 {
    font-weight: 300;
    font-size: 38px;
    margin-bottom: 3rem;
  }

  h2 {
    font-weight: 600;
    font-size: 24px;
  }

  h5 {
    font-weight: 500;
    color: rgb(191, 191, 191);
  }

  body {
    min-height: 100vh;
  }
}
</style>