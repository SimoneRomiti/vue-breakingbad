<template>
   <div class="box-container">
      <router-link :to="{name: 'Show', params:{id: character.char_id}}" class="router" v-for="character, index in characters" :key="index">
         <div class="box">
        
            <img :src="character.img" alt="">
            <div class="eye">
               <i class="far fa-eye"></i>  
            </div>
            <div class="box-body">
               <h2>{{ character.name }}</h2>
            </div>
         </div>
      </router-link>
      <button class="btn btn-primary" @click="sendSee" v-if="hide == false">Vedi tutti</button>
      <button class="btn btn-primary" @click="sendHide" v-else>Nascondi</button>


      
      
   </div>
 
</template>

<script>
export default {
   name: 'Cards',
   props: ['characters'],

   data(){
      return {
         hide: false
      }
   },
  
  methods: {
     sendSee(){
        this.$emit('see');
        const self = this;
        setTimeout( function(){
        self.hide = true;
        }, 300)
     },

     sendHide(){
         this.$emit('hide');
         const self = this;
         setTimeout( function(){
         self.hide = false;
         }, 300)
     }
  }

}
</script>

<style lang="scss" scoped>
   .box-container{
      display: flex;
      flex-wrap: wrap;
      padding: 50px;

      button{
         height: 50px;
         align-self: center;
         margin-left: 100px;
      }

      .router{
         width: calc(100% / 4 - 40px);
         margin: 20px;
      }

      .box{
         width: 100%;
         box-shadow: 10px 10px 10px #303030;
         transition: all .3s;
         position: relative;

         &:hover{
            transform: scale(1.1);
            cursor: pointer;

         }

         &:hover img{
            filter: blur(3px);
         }

         &:hover .eye{
            opacity: 1;
         }

         .eye{
            width: 50px;
            height: 50px;
            border: 1px solid #6CB983;
            border-radius: 3px;
            font-size: 40px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #6CB983;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
         }

         img{
            width: 100%;
            object-fit: cover;
            object-position: top;
            height: 300px;
         }

         .box-body{
            margin: 15px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 5px;
            color: white;
            position: absolute;
            bottom: 0;

            h2{
               margin: 0;
            }
         }
      }
   }
</style>