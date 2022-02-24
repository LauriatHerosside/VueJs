
<template>
  <table border="1px" >
    <tr>
      <td>Id </td>
      <td>Date emprunt</td>
      <td>Date retour</td>
      <td>id_chaises</td>
      <td>id_personnes</td> 
    </tr>
     <tr v-for="emprunt in emprunt" :key="emprunt.id" >
      <td>{{emprunt.id}} </td>
       <td>{{emprunt.date_retour}}</td>
      <td>{{emprunt.date_emprunt}}</td>
      <td>{{emprunt.id_chaises}}</td>
      <td>{{emprunt.id_personnes}}</td>
        
    </tr>
  </table>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'
// axios librairie pour faire les requetes HTTP
import axios from 'axios';
export default {
  name: "App",
  components: {},
//Declaration des variables(data)
  data() {
    return {
      emprunt:[]
    }
  },
  // Methode appelée quant le composant est chargé(page)
  mounted() {
     axios
      .get("http://127.0.0.1:8000/emprunt/emprunt-list/")
      .then((response) => {
        this.emprunt = response.data;
        console.warn(response)
      })
      .catch((error) => {
        console.log(error);
      });
  },}
</script>
<style>
#app {
  margin-left: auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 20px;
  font-weight: bold;
}
ul {
  list-style: none;
  display: flex;
  text-align: center;
  justify-content: center;
}
ul,
li {
  margin: 10px;
  font-size: 20px;
  color: gray;
}
a {
  color: red;
  text-decoration: none;
}
a:hover {
  color: #fff;
}
#title {
  text-align: center;
  font-size: 30px;
}
</style>