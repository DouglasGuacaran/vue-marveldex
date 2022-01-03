<template>
<b-row class="">
    <b-card
    class="card"
    :img-src="`${thumbnailPath}.${thumbnailExtension}`" :alt="`${name}`" img-height="500">
    <h3 class="texto">Nombre: {{ name }}</h3>
    <h5 class="texto">Modificado: {{ date }}</h5>
    <b-button @click="close()">Cerrar</b-button>
    </b-card>
</b-row>
    
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "Card",
  components:{
  },
  props: {
    name: String,
    thumbnailPath: String,
    thumbnailExtension: String,
    description: String,
    date: String,
    index: String
  },
  methods: {
    ...mapActions(['editHeroAction', 'hideCardHeroAction']),
    editarCard() {
      this.editHeroAction(this.index);
    },
    close(){
      this.hideCardHeroAction();
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@700&display=swap');

.texto{
  font-family: "Roboto Condensed";
}

#img{
  padding: 0;
}

</style>
