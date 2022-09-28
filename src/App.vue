<template>
  <div>
    <button @click="roll">roll</button>
    <p> Resultado: {{dice}} </p>
    <div v-if="dice != 0">
      <img :src="selected"/>
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
        selected: '',
        dice: 0,
      }
    },
    created(){
      this.selected = this.img[1];
    },methods:{
      roll: function(){
      this.dice = Math.ceil(Math.random() *6);
      this.selected = new URL('./components/icons/'+ this.img[this.dice-1], import.meta.url).href;
      console.log(this.selected);
      }
    }
  }
</script>