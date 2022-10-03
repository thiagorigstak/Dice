<template>
    <div class="container-fluid">
      <H1>
        <button type="button" class="btn btn-dark btn-lg" @click="roll">🎲 roll 🎲</button>
      </H1>
      <div v-if=" dice1 > dice2">
        <p> 🚩 Player 1 Ganhou </p>
      </div>
      <div v-else-if=" dice2 > dice1">
        <p> Player 2 Ganhou 🚩</p>
      </div>
      <div v-else>
        <p>🎲 Empate 🎲</p>
      </div>
      <div class="row">
        <div class="col-sm">
          <img :src="selected1"/>
        </div>
        <div class="col-sm">
          <img :src="selected2"/>
        </div>
      </div>
    </div>
</template>

<script>
  export default {
    data(){
      return{
        img: [
          'dice1.png',
          'dice2.png',
          'dice3.png',
          'dice4.png',
          'dice5.png',
          'dice6.png',
        ],
        selected1: '',
        selected2: '',
        dice1: 0,
        dice2: 0,
      }
    },
    created(){
      this.selected1 = this.img[0];
      this.selected2 = this.img[0];
      this.roll();
    },methods:{
      roll: function(){
      this.dice1 = Math.ceil(Math.random() *6);
      this.dice2 = Math.ceil(Math.random() *6);
      this.selected1 = new URL('./components/icons/'+ this.img[this.dice1-1], import.meta.url).href;
      this.selected2 = new URL('./components/icons/'+ this.img[this.dice2-1], import.meta.url).href;
      console.log(this.selected1, this.selected2);
      }
    }
  }
</script>

<style>
  p {
    font-size: 2rem;
    color: #015338;
    font-family: 'Indie Flower', cursive;
  }
  h1 {
    margin: 30px;
    font-family: 'Lobster', cursive;
    text-shadow: 5px 0 #232931;
    font-size: 8rem;
    color: #4ECCA3;
  }
</style>