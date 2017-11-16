<template>
  <div class="mdl-layout mdl-js-layout mdl-layout--fixed-header">
    <header class="mdl-layout__header">
      <div class="mdl-layout__header-row">
        <span class="mdl-layout-title">CFG Symag</span>
        <router-link class="mdl-navigation__link" to="/" >
          <i class="material-icons">home</i>
        </router-link>
      </div>
    </header>
    <div class="mdl-layout__drawer">
      <span class="mdl-layout-title">CFG Symag</span>
      <nav class="mdl-navigation">
        <router-link class="mdl-navigation__link" to="/" @click.native="hideMenu">Liste des magasins</router-link>
        <router-link class="mdl-navigation__link" to="/ajout" @click.native="hideMenu">Ajout d'un magasin</router-link>
        <a v-if="this.$cookie.get('idUtilisateur')" class="mdl-navigation__link" @click.prevent="deconnexion">Déconnexion</a>
        <router-link v-else class="mdl-navigation__link" to="/connexion" @click.native="hideMenu">Connexion</router-link>
      </nav>
    </div>
    <main class="mdl-layout__content">
      <div class="page-content">
        <router-view></router-view>
      </div>
    </main>
  </div>
</template>

<script>
require('material-design-lite')
export default {
  name: 'app',
  methods: {
    hideMenu: function () {
      document.getElementsByClassName('mdl-layout__drawer')[0].classList.remove('is-visible')
      document.getElementsByClassName('mdl-layout__obfuscator')[0].classList.remove('is-visible')
    },
    verifConnexion () {
      if (this.$cookie.get('idUtilisateur')) {
        this.$router.push('/')
      } else {
        this.$router.push('/connexion')
      }
    },
    deconnexion () {
      this.$cookie.delete('idUtilisateur')
      this.verifConnexion()
    }
  },
  mounted () {
    this.verifConnexion()
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/icon?family=Material+Icons');
  @import url('https://code.getmdl.io/1.2.1/material.blue-red.min.css');
  .mdl-layout__header {
    background-color: rgb(0,134,89);
  }
</style>
