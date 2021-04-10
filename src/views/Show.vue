<template>
  <div>
    <div class="container">
      <div class="card mb-3">
        <div class="row no-gutters">
          <div class="col-md-6">
            <img :src="character.img" alt="" style="width: 100%">
          </div>
          <div class="col-md-6">
            <div class="card-body">
              <h2 class="card-title">{{ character.name }}</h2>
              <p class="card-text">Nickname: <strong>{{ character.nickname }}</strong></p>
              <p class="card-text">Interpretato da: <strong>{{ character.portrayed }}</strong></p>
              <p class="card-text">Seasons appearances:
                <strong>
                  <ul>
                    <li v-for="season, index in character.appearance" :key="index">season {{ season }}</li>
                  </ul>
                </strong>
              </p>
              <p class="card-text">Stato attuale: <strong>{{ translation }}</strong></p>

              <Death :data="character" v-if="visible" />
            </div>
          </div>
        </div>
      </div>
    </div>

    
  </div>
  
</template>

<script>
import Death from '../components/Death.vue'

export default {
   name: 'Show',
   components: {
     Death
   },

   data(){
     return{
       character: '',
       transaltion: '',
       visible: false
     }
   },
   
   mounted(){
     let url = window.location.href;
     url = url.split('/');
     const id = url[url.length-1];
     console.log(id);

     this.axios
      .get(`https://www.breakingbadapi.com/api/characters/${id}`)
      .then(response => {
        console.log(response);
        this.character = response.data[0];
        console.log(this.character.status);
        if(this.character.status == 'Alive'){
          this.translation = 'Vivo';
        } else{
          this.translation = 'Morto';

          
            this.visible = true;

              
        }

      })
     
   }
}
</script>

<style lang="scss">
  li{
    list-style: none;
  }
</style>