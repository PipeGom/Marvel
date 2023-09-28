<template >
 
  <center>
  <h1>Characters</h1>
</center>
  <v-sheet
class="d-flex align-content-end justify-center flex-wrap  "
style="background-image: url('https://e0.pxfuel.com/wallpapers/789/909/desktop-wallpaper-dc-comic-book-covers-marvel-and-dc-comics.jpg');
 "
  >
  <v-card
  v-for="item in characters"
              :key="item.id"
      class="ma-4 pa-4"
      style="background-color: rgb(0, 141, 184);"

  
  >
  
    <v-card-text>
      <v-img
      :src="(`${item.thumbnail.path}/detail.${item.thumbnail.extension}`)"
      height="450px"
      width="300px"
      cover
    ></v-img>
    <p>{{ item.name }}</p>
    </v-card-text>
      
   

      <v-dialog
        transition="dialog-bottom-transition"
        width="20%"

       
      >
        <template v-slot:activator="{ props }">
          <v-btn
            color="blue"
            v-bind="props"
           
          >See more</v-btn>
          
    
        </template>
    
        <template v-slot:default="{ isActive }">
         
          <v-card>
            <v-toolbar
              color="cyan"
              :title="item.name"
            ></v-toolbar>
            <v-card-text>

              <v-img
      :src="(`${item.thumbnail.path}/detail.${item.thumbnail.extension}`)"
      height="200px"
      width="100%"
      cover
    ></v-img>
           
            <h1>Description</h1>
            <v-card-text v-if=" item.description !== '' ">
              <p>{{ item.description }}</p>
            </v-card-text>
            <v-card-text v-else>
              <p>N/A</p>
            </v-card-text>
            <h1>
              Comics
            </h1>
            <v-card-text >
              <p>{{ item.comics.available }}</p>
            </v-card-text>

            <h1>
              Series
            </h1>
            <v-card-text >
              <p>{{ item.series.available }}</p>
            </v-card-text>

            <h1>
              Stories
            </h1>
            <v-card-text >
              <p>{{ item.stories.available }}</p>
            </v-card-text>

            <h1>
              Events
            </h1>
            <v-card-text >
              <p>{{ item.events.available }}</p>
            </v-card-text>

            <h1>
              outstanding series
            </h1>
            <v-card-text v-for="(series,index) in item.series.items">
              <p v-if="index < 3"> {{ series.name }}</p>
            </v-card-text>

            
        
            </v-card-text>
            <v-card-actions class="justify-end">
        
              <v-btn
                variant="text"
                @click="isActive.value = false"
              >Close</v-btn>
            </v-card-actions>
          </v-card>
         
        </template>
      
      </v-dialog>
   

   
  </v-card>

  </v-sheet>

  
  
</template>

<style>
h1{
  font-family: Impact, fantasy;
  
}
p {
  font-weight: 500;
  font-family: Didot, serif;
  font-size: x-large;
  text-align: center;
}


</style>

<script  setup >


import axios from "axios";


const characters = ref([ ])

onBeforeMount( ()=>{
   loadCharacters()
})

const loadCharacters = async () =>{

  const url = "https://gateway.marvel.com/v1/public/characters?ts=1&apikey=2aaf9becdbbb17f3a5336e113557e58c&hash=01230b37293496e3c668ada1812633af&limit=60"
  const { data } = await axios.get(url)  // Desturcturar la data
  characters.value = data.data.results
  
  console.log(characters.value)
  console.log(characters.value.description)

}
</script>

<script>
  export default {
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>





