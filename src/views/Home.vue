<template>
  <div class="home">
   <h1>This is an home page</h1>
  </div>
</template>

<script>
// @ is an alias to /sr


export default {
  name: "Home",
  components: {
    
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
      })
  }
};
</script>
