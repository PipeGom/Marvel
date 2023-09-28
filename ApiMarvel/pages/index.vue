<template>
     <v-sheet
class="d-flex align-center justify-center flex-wrap flex-column "
style="background-image: url('https://e0.pxfuel.com/wallpapers/789/909/desktop-wallpaper-dc-comic-book-covers-marvel-and-dc-comics.jpg');
 height: 100vh;"
  >
  <div  style="background-color: rgb(173, 61, 61); width: 70%;">
  <nuxt-link to="/characters" style="font-weight: 500;
  font-family: Didot, serif;
  font-size: xx-large;
  text-align: center;
  text-decoration: dotted;
  padding-inline: 15% 10%;
  padding-top: 0%;
  padding-left: 0%;
  margin-top: 0%;
  margin-bottom: 0%;
  color: azure;
  ">
<center>Go to character catalog
</center>

  </nuxt-link>
</div>
  <v-carousel show-arrows="hover" class="carousel">
  <v-carousel-item
    src="/img1.jpeg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="/imagen2jpg.jpg"
    
  ></v-carousel-item>

  <v-carousel-item
    src="img3.jpg"
    
  ></v-carousel-item>
</v-carousel>
</v-sheet>

<nuxt-link to="/characters">
link
</nuxt-link>

</template>
<style>
.carousel{
  max-width: 70%;
  align-items: center;
  background-color: black;
}
</style>