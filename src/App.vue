<template>
  <div id="app">
    <v-form></v-form>
  </div>
</template>

<script>
import VForm from './components/vForm.vue';

export default {
  name: 'app',
  components:{
    VForm
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500&display=swap');

  html {
    background: #E5E5E5;
  }

  body {
    margin: 0;
    padding: 0;
  }

  #app{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
  }
</style>
