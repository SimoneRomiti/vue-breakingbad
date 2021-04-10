<template>
  <div id="death">
      <h4>Death</h4>
      <p class="card-text">Causa: <strong>{{ death.cause }}</strong></p>
      <p class="card-text">Killer: <strong>{{ death.responsible }}</strong></p>
      <p class="card-text">Ultime parole: <strong>{{ death.last_words }}</strong></p>
   </div>
</template>

<script>
export default {
   name: 'Death',
   props: ['data'],

   data(){
      return {
         death: {}
      }
   },

   mounted(){
      this.axios
         .get(`https://www.breakingbadapi.com/api/death?name=${this.data.name}`)
         .then(response => {
            console.log(response);
            this.death['cause'] = (response.data[0].cause);
            this.death['responsible'] = (response.data[0].responsible);
            this.death['last_words'] = (response.data[0].last_words);

            this.$forceUpdate();
         })
   }

}


</script>

<style>

</style>

