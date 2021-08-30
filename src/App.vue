<template>
  <div id="app">
    <Contenitore/>
  </div>
</template>

<script>
import Contenitore from '@/components/Contenitore.vue';

export default {
  name: 'App',
  components: {
    Contenitore
  }
}
</script>

<style lang="scss">
@import 'assets/scss/general.scss';
#app{
  background-color: #040343;
  height: 100vh;
}
</style>
