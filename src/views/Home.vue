<template>
  <div class="home">
   <h1>This is an home page</h1>
   <BaseInput @sendit="searchByName" />
   <Cards :characters="characters" @see="seeAll" @hide="hide" />
  </div>
</template>

<script>
// @ is an alias to /sr
import Cards from '../components/Cards.vue';
import BaseInput from '../components/BaseInput.vue';

export default {
  name: "Home",
  components: {
    Cards,
    BaseInput
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
  },

  methods: {
    searchByName(payload){
      this.axios
        .get(`https://www.breakingbadapi.com/api/characters?name=${payload}&limit=10`)
        .then(response => {
          this.characters = response.data;
        })
    },

    seeAll(){
      this.axios
      .get('https://www.breakingbadapi.com/api/characters')
      .then(response => {
        console.log('response');
        this.characters = response.data;
      })
    },

    hide(){
      this.axios
        .get('https://www.breakingbadapi.com/api/characters?limit=10')
        .then(response => {
          console.log(response);
          this.characters = response.data;
        })
    }
  }
};
</script>
