<template>
 
     <div class="row my-4">
      <div class="col-md-6 mx-auto">
        <div class="form-group">
          <input type="text" class="form-control"
          autocomplete="off"
          placeholder="Entrer une ville"
          id="address-input">
       
        </div>
      </div>
     </div>
</template>

<script>
// hiya un fois katcharga la page kankhdmo b raective
import { onMounted,reactive } from 'vue';
import places from 'places.js';
export default {
  name:"Search",
  // kisayft wa7d l event lihowa 
  emits:["search-result"],
  //emit kan recoperiwha mn lprops hiya bach knkhdm b emit
  setup(props,{emit}){
    const state=reactive({
      appId:"pl84BDTK7HU7",
      apikey:"671cd803cf905b98ff3217c773e5207a"
     });
     function getPlaces(){
      let placesAutocomplete=places({
        appId:state.appId,
        apiKey:state.apikey,
        //container howa champ lighadi it afficha lina fih l result
        //katgolih had documentli l id dyalo address-input hiya fin ghadi nafficher ville dyalna
        container:document.querySelector('address-input')
      })
      //kif atchanga had placesAutocomplete farah ghadi t executer had l function
      placesAutocomplete.on("change",function($e){
      //mni ghadi t executa liya had l event farah ghadi nsayftoha l parent Home bl function emit
      //had suggestion li9tira7at li3adna
      emit("search-result",$e.suggestion)
      });
     }
     onMounted(()=>{
      getPlaces();
     })
     return {

     };
  }
     
}
</script>
<style scoped>

</style>
