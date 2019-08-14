<template>
  <div class="menu">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-container>
        <b-navbar-brand><nuxt-link to="/"><img src="https://cdn.bulbagarden.net/upload/4/4b/Pok%C3%A9dex_logo.png" alt="" class="logo"></nuxt-link></b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto"></b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-item href="#">
              <router-link to="/">Inicio</router-link>
            </b-nav-item>

            <b-nav-item href="#">
              <router-link to="/categorias">Pokemon Types</router-link>
            </b-nav-item>

            <b-nav-item href="#">
              <router-link to="generacion">Generacion</router-link>
            </b-nav-item>

            <b-nav-form class="ml-3">
              <b-form-input type="text" min="0.00"></b-form-input>

              <b-input-group-append>
                <b-button variant=""><i class="fas fa-search-plus"></i></b-button>
              </b-input-group-append>
            </b-nav-form>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
  </div>
</template>

<style lang="scss">
.logo {
  height: 50px
}

.bg-info {
  background: #FF615C !important;
}

.nav-item {
  .nav-link a {
    color: white;
  }

  .nuxt-link-exact-active {
    color: white;

    opacity: 0.8;
  }
}
</style>