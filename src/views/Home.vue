<template>
  <b-container>
    <b-row class="mt-4" >
      <b-col xs="12" align="center" class="mx-auto">
        <h1>Bienvenidos a mi página sobre Marvel</h1>
        <b-img class="image" :src="require('../assets/Images/The_Marvel_Universe.png')"></b-img>
        <h2>Donde podrás conocer los datos de algunos de los personajes emblemáticos del Universo Marvel</h2>
        <b-button class="mt-3" variant="warning" @click="$router.push('/marveldex')">Adelante</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style>
  .image{
    width: 90%;
  }

  @media screen and (max-width:690px) {
    .image{
      width: 85%;
    }
    
  }
</style>

