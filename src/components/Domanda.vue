<template>
<div>
  <div class="row"
  v-if="!flagPartita"
  >
    <div class="col-xs-12">
      <h1>{{this.domanda}}</h1>
    </div>
    <div class="col-xs-12 col-md-6 risposta"
    v-for="(risposta, index) in risposte" :key="index"
    @click="RispostaGiusta(risposta)"
    >
      <h1>{{risposta.risposta}}</h1>
    </div>
  
   <!--  <button @click="v()">
      clicca
    </button> -->
  </div>
  <div class="row"
  v-else
  >
    <div class="alert alert-danger" role="alert">
      risposta errata
    </div>
    <h1>Partita Persa</h1>
    <button @click="NewGame()">
      New Game
    </button>
  </div>
</div>
</template>

<script>
import qf from '@/assets/data/domande.js';

export default {
  name: 'Domanda',
 /*  props:{
    domanda: String
  }, */
  data(){
    return{
      qf,
      domanda : "",
      risposte : [], 
      min : 0,
      max : 14,
      indici : [],
      flagPartita : false
    }
  },
  created(){
    let r = this.getRandomIntInclusive(this.min, this.max); //indice che prende un numero random tra 0 e 14 (nuemro di domande presenti nel nostro file js) 
    this.domanda = this.qf[r].domanda; //salvo nella variabile domanda il contenuto in posizione r attributo domanda di qf (file che contiene le nostre domande)
    this.risposte = this.qf[r].rs;
    this.indici.push(r);
    console.log(this.indici);
    console.log(this.risposte)
  }
  ,
  methods:{
    v(){
      console.log(this.qf);
    },
   /*  VisualizzaDomanda(){
      let r = this.getRandomIntInclusive(this.min, this.max);
      this.domanda = qf[r].domanda;
    }, */
    getRandomIntInclusive(min , max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min + 1) + min); //The maximum is inclusive and the minimum is inclusive
    },
    RispostaGiusta(risposta){
      let r;

      if(!risposta.flag){
        /* alert("errore"); */
        this.flagPartita = true
      }else{
         do{
          r = this.getRandomIntInclusive(this.min, this.max);
          console.log(r);
          console.log(this.indici)
      }while(this.indici.includes(r));
      this.indici.push(r)
      console.log(this.indici)
      this.domanda = this.qf[r].domanda;
      this.risposte = this.qf[r].rs;

      /* PARTE DA RIPARARE + AGGIUNGERE TABELLONE MONTEPREMI CHE SI ILLUMINA IN BASE ALLA DOMANDA NELLA QUALE CI TROVIAMO (prima domanda primo montepremi seconda domanda secondo montepremi ecc) */
      }
    },
    NewGame(){
      /* this.domanda = "";
      this.risposte = [];
      this.indici = [];
      this.flagPartita = false;
      newDom(); */
      location.reload();
    },
    /* newDom(){
      let r = this.getRandomIntInclusive(this.min, this.max); //indice che prende un numero random tra 0 e 14 (nuemro di domande presenti nel nostro file js) 
      this.domanda = this.qf[r].domanda; //salvo nella variabile domanda il contenuto in posizione r attributo domanda di qf (file che contiene le nostre domande)
      this.risposte = this.qf[r].rs;
    this.indici.push(r);
    console.log(this.indici);
    console.log(this.risposte)
    } */
  }
}
</script>

<style lang="scss" scoped>
.domanda-c{
  
}
.risposta{
  border: 1px solid white;
  &:hover{
    background-color: yellow;
  }
  &:active{
    background-color: green;
  }
}
</style>

