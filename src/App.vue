<template>
  <div id="app">
    <h1>Моя галерея фильмов</h1>
    <SearchMain v-bind:cards="cards"/>

    <hr> 

    <CreateMain 
    @add-card="addCard"
    />


  </div>
</template>


<script>
  import SearchMain from '@/components/SearchMain'
  import CreateMain from '@/components/CreateMain'
  const axios = require('axios');
  export default {
    name: 'App',
    data() {
      return {
        cards: [
        {id: 1, name: 'Кинг-Конг', year: 2020, favorite: false},
        {id: 2, name: 'Симбад Легенда Семи морей', year: 2020 , favorite: false},
        {id: 3, name: 'Социальная сеть', year: 2020, favorite: true}
        ]
      }
    },
    methods:{
      addCard(card){
        axios.post('http://localhost:3000/api/Movies', {
          name: card.name,
          year: card.year,
          favorite: card.favorite
        });
        axios.get('http://localhost:3000/api/Movies')
        .then(response => {
         this.cards = response.data 
       })
        .catch(function(e){
          this.error = e;
        });
      }
    },
    mounted() {

      axios.get('http://localhost:3000/api/Movies')
      .then(response => {
       this.cards = response.data 
     })
      .catch(function(e){
        this.error = e;
      });
    },
    components: {
      SearchMain: SearchMain,
      CreateMain
    }
  }


</script>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  transition: .5s;
}
</style>
