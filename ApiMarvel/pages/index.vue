<template>
      <center>
    <h1>Characters</h1>
  </center>
<v-sheet
class="d-flex align-content-end flex-wrap  "
  >
  <v-card
  v-for="item in characters"
              :key="item.id"
      class="ma-4 pa-4"
      style="background-color: rgb(0, 141, 184);"
  >
    <v-img
      :src="(`${item.thumbnail.path}/detail.${item.thumbnail.extension}`)"
      height="450px"
      width="300px"
      cover
    ></v-img>

    <v-card-title>
      {{ item.name }}
    </v-card-title>

    <v-card-subtitle>
      Id: {{ item.id }} 
    </v-card-subtitle>

    <v-card-actions>
      <v-btn
        color="black-lighten-2"
        variant="text"
      >
        Explore
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
        :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show = !show"
      ></v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
        </v-card-text>
      </div>
    </v-expand-transition>

  </v-card>
</v-sheet>


</template>

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

}
</script>
<script>
export default {
    data: () => ({
      show: false,
    }),
  }
</script>