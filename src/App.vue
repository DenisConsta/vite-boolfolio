<script >
import axios from "axios";

import AppCard from "./components/AppCard.vue";

  export default{
    name: 'App',
    components: {
      AppCard,

    },  
    data(){
      return{
        projects: [],
        basicUrl: 'http://127.0.0.1:8000/api/',
      }
    },
    methods:{
      getApi(){

        axios.get(this.basicUrl + 'projects', {
            params:{              
            }
          })
          .then((result) => {
            this.projects = result.data.projects;
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
    mounted(){
      this.getApi();
    }
  }

</script>

<template>
  <h1 class="display-1">Hello Vue!</h1>  

  <div class="container">
    <div class="row">
      <div v-for="project in projects" :key="project.id" class="col-3 mb-3">
        <AppCard :project="project"/>
      </div>
    </div>
  </div>

</template>

<style scoped lang="scss">
@use './styles/general.scss' as *;

h1{
  color: red;
}

</style>
