<template>
  <div class="home">
   <h1>This is an home page</h1>
   <Cards :characters="characters" />
  </div>
</template>

<script>
// @ is an alias to /sr
import Cards from '../components/Cards.vue';

export default {
  name: "Home",
  components: {
    Cards
  },

  data(){
    return{
      characters: []
    }
  },

  mounted(){
    this.axios
      .get('https://www.breakingbadapi.com/api/characters?limit=10')
      .then(response => {
        console.log(response);
        this.characters = response.data;
      })
  }
};
</script>
