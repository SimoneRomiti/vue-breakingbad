<template>
  <div>
     <div class="form-group mt-5 mb-2">
      <input type="text" class="m-auto form-control" id="search" v-model="searched" @keyup="sendSearch" style="width: 40%" placeholder="Search Characters">
  </div>
     
  </div>
</template>

<script>
export default {
   name: 'BaseInput',

   data(){
      return{
         searched: ''
      }
   },

   methods:{
      sendSearch(){
         this.$emit('sendit', this.searched);
      }
   }
}
</script>

<style>

</style>