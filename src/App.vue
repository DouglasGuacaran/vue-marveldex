<template>
  <div id="app">
    <b-navbar class="navbar" toggleable="lg" type="dark">
      <b-navbar-brand href="#"><router-link to="/">Inicio </router-link> </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item> <router-link to="/marveldex">MarvelDex</router-link> </b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <router-view/>
  </div>
</template>


<script>
export default {
  name:'Navbar'

}
</script>



<style>
#app > nav > a > a { 
  color: #EC1D24;
  text-decoration: none;
  margin-left: 10px ;
}
#nav-collapse > ul > li > a > a {
  color: #EC1D24 ;
  text-decoration: none;
}

.navbar{
  background-color:#202020 ;
}

</style>
