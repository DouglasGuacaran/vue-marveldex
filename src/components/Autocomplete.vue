<template>
  <b-row>
    <b-col>
      <b-row>
        <b-col @keyup.enter="submit()">
          <vue-bootstrap-typeahead
            :data="this.listOfNames"
            placeholder="Escriba el nombre del personaje..."
            v-model="name"
          />
        </b-col>
      </b-row>
      <b-row align-h="center">
        <b-col class="p-0 m-1" cols="3">
          <b-button
            class="text-center texto"
            size="sm"
            type="submit"
            @click="requestHero()"
            @keyup.enter="submit()"
          >
            Buscar
          </b-button>
        </b-col>
      </b-row>
    </b-col>
  </b-row>
</template>

<script>
import listOfName from "../assets/Json/ListOfHero.json";
import { mapActions } from "vuex";
export default {
  data() {
    return {
      name: "",
      listOfNames: [],
    };
  },
  components: {
    listOfName,
  },
  computed: {},
  methods: {
    ...mapActions(["getHeroAction", "getListOfNameAction"]),
    mountListOfNames() {
      this.listOfNames = listOfName;
    },
    submit() {
      this.getHeroAction(this.name);
    },
    requestHero() {
      this.getHeroAction(this.name);
    },
  },
  mounted() {
    this.mountListOfNames();
    this.getListOfNameAction();
  },
};
</script>

<style>
</style>