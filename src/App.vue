<template>
  <main class="container">
    <Header />
  </main>
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: "Poppins", sans-serif;
}

.container{
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  padding: 0 10px;
}
</style>
