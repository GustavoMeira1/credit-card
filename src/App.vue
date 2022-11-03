<template>
  <v-app>
    <clonas/>
  </v-app>
</template>

<script>
import clonas from './components/clonas.vue';

export default {
  name: 'App',

  components: {
    clonas,
  },
};
</script>

<style>
@media only screen and (max-width: 400px) {
#app{
  display: flex;
  position: relative;
  background-image: url(./images/bg-main-mobile.png) ;
  background-repeat: no-repeat;
}
}
@media only screen and (min-width: 400px) {
#app{
  display: flex;
  position: relative;
  background-image: url(./images/bg-main-desktop.png) ;
  background-repeat: no-repeat;
}
}
</style>
