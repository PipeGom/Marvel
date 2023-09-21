<template>

<v-sheet
class="d-flex align-content-end flex-wrap  "
  >
    <v-sheet 
      v-for="item in characters"
              :key="item.id"
      class="ma-2 pa-2"
    >
    <v-img  
    :src="(`${item.thumbnail.path}/standard_amazing.${item.thumbnail.extension}`)"
    height="450px"
    width="300px"
    cover
    ></v-img>
    Id: {{ item.id }} - Name: {{ item.name }}
    </v-sheet>
  </v-sheet>




</template>
<script  setup >
import axios from "axios";

const characters = ref([])

onBeforeMount( ()=>{
     loadCharacters()
})

const loadCharacters = async () =>{

    const url = "https://gateway.marvel.com/v1/public/characters?ts=1&apikey=2aaf9becdbbb17f3a5336e113557e58c&hash=01230b37293496e3c668ada1812633af"
    const { data } = await axios.get(url)  // Desturcturar la data
    characters.value = data.data.results
    
    console.log(characters.value)

}
</script>