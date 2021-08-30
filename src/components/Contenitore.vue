<template>
  <div class="container d-flex flex-column align-content-center">
    <h1 class="text-center mb-4">Chi vuol essere Stronzolo?</h1>
    <img class="" src="~@/assets/img/logo.png" alt="">
    <Domanda
    />
    
  </div>
</template>


<script>
import Domanda from './Domanda.vue';

export default {
  name: 'Contenitore',
  components:{
    Domanda,
  },
  data(){
    return{
    }
  }
}
</script>

<style lang="scss" >
.container{
  margin:0;
  padding: 0;
  height: 100vh;
  background-image: linear-gradient(to right,#1917d0, #2a0861);
  color:white;
  img{
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
    margin-bottom: 30px;
    height: 200px;
    width: 200px;
}
}

</style>