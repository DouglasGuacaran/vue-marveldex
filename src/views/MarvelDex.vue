<template>
  <b-container>
    <b-row v-if="showCardHero" align-h="center">
      <b-col
        cols="12"
        class="text-center formularioConsulta"
        v-for="(item, index) in Hero"
        :key="index + 'A'"
      >
        <CardHero
          :name="item.name"
          :thumbnailPath="item.thumbnailPath"
          :thumbnailExtension="item.thumbnailExtension"
          :description="item.description"
          :date="item.dateFormat"
        />
      </b-col>
    </b-row>
    <b-row align-h="center" class="justify-content">
      <b-col cols="3">
        <b-img
          src="https://logos-marcas.com/wp-content/uploads/2020/11/Marvel-Logotipo-2012-2014.jpg"
          fluid
          alt="Logo Marvel"
        ></b-img>
      </b-col>
      <b-col cols="4">
        <span class="texto">Buscar Personaje:</span>
        <Autocomplete />
      </b-col>
    </b-row>
    <b-row v-if="showForm" class="formularioEditar" align-h="center">
      <b-col cols="10" align-h="center">
        <span class="texto">Nombre del Personaje:</span>
        <b-form-input class="text-center" v-model="currentEdit.name">
        </b-form-input>
        <span class="texto">Descripcion:</span>
        <b-form-input class="text-center" v-model="currentEdit.description">
        </b-form-input>
        <b-row align-h="center" class="m-3">
          <b-col cols="4"
            ><b-button class="btn btn-button" @click="aceptarCambios()"
              >Aceptar</b-button
            ></b-col
          >
        </b-row>
      </b-col>
    </b-row>

    <b-row v-if="noCardHero">
      <b-col>
        <h1 class="texto">
          {{ this.Hero.name }} no se encuentra en la base de datos
        </h1>
      </b-col>
    </b-row>
    <b-row align-h="center">
      <b-col
        lg="5"
        md="3"
        sm="7"
        class="text-center cards"
        v-for="(item, index) in listOfHeroes"
        :key="index + 'B'"
      >
        <CardHeroes
          :name="item.name"
          :thumbnailPath="item.thumbnailPath"
          :thumbnailExtension="item.thumbnailExtension"
          :description="item.description"
          :date="item.dateFormat"
          :index="index.toString()"
        />
      </b-col>
      <infinite-loading @infinite="getHeroesAction"></infinite-loading>
    </b-row>
    <b-row v-if="isLoading" class="loading m-3" align-h="center">
      <b-col cols="1" align-h="center">
        <h2 class="texto">Loading...</h2>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import InfiniteLoading from "vue-infinite-loading";
import CardHero from "../components/CardHero.vue";
import CardHeroes from "../components/CardHeroes.vue";
import { mapState, mapActions } from "vuex";
import Autocomplete from "../components/Autocomplete.vue";
export default {
  name: "MarvelDex",
  data() {
    return {};
  },
  components: {
    Autocomplete,
    CardHero,
    CardHeroes,
    InfiniteLoading,
  },
  computed: {
    ...mapState([
      "listOfHeroes",
      "isLoading",
      "showForm",
      "pagina",
      "currentEdit",
      "Hero",
      "showCardHero",
      "noCardHero",
    ]),
  },

  methods: {
    ...mapActions(["changeOnStoreAction", "getHeroesAction"]),
    aceptarCambios() {
      this.changeOnStoreAction();
    },
  },
  mounted() {},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@700&display=swap");

.loading {
  background: #ffff;
  align-content: center;
  height: 400px;
  width: 1250px;
}
.formularioConsulta {
  position: fixed;
  width: 500px;
  height: 200px;
  z-index: 100;
}
.formularioEditar {
  color: white;
  position: fixed;
  width: 500px;
  height: 200px;
  background: black;
  z-index: 100;
  border-radius: 10px;
  right: 0;
  left: 0;
  margin: auto;
}

.texto {
  font-family: "Roboto Condensed";
}
</style>
