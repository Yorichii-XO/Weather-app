<template>
  <div class="container">
   <!-- hna ghadin recoperiw l event lisayftna-->
<Search @search-result="getWeather"/>
  </div>
 </template>
 
 <script>
 import Search from './Search';
 export default {
   name: 'HomePage', 
   //hna madam ecoperitih adiro fl components
  components:{Search},
  setup(){
    const state=reactive({
      weather:null,
      data:null,
      key:"1d5cfbb4b1ba74f6287033207b5f59d7"
    })

   async function getWeather(city){
    //bach nricopiriwles donnes mn dark ski l api fa ilaz recobirinaha mn domain li bara dyal domain dyalna
  //farah krome nichan ki blokiha 7it la aapel liijaya f wa7d domain la 3la9a b bhad domain hada 
  // ki3tk errir lihowa cross origin= bloked cross origin
  // bach ntfadawha farah daro wa7d l application smitha cros-anywhere lim7tota f herokuapp
  //herokuapp howa iberjour web
  const proxy="https://cros-anywhere.herokuapp.com/"
const apiUrl=`https://api.darksky.net/forecast/${state.key}/${city.lat}/${city.latlng.lng}?lang=fr&units=ca`   
const data=await fetch(proxy+apiUrl);
const resData=await data.json();
}
  }
  return{
    getWeather,
    }
  }
 </script>
 

 <style>
 </style>
 