<template>
  <div>
    <img :src="character.img" alt="">
    <h1>{{ character.name }}</h1>
    <p>{{ character.portrayed }}</p>
    <p>{{ character.nickname }}</p>
  </div>
  
</template>

<script>
export default {
   name: 'Show',

   data(){
     return{
       character: ''
     }
   },
   
   mounted(){
     this.character = this.$route.params.data;
   }
}
</script>

<style>

</style>