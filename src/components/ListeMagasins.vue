<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <div>
      <div class="mdl-grid">
        <!-- <div class="mdl-cell mdl-cell--3-col mdl-cell mdl-cell--1-col-tablet mdl-cell--hide-phone"></div> -->
        <div class="mdl-cell mdl-cell--12-col mdl-cell--12-col-phone">
          <div v-for="magasin in this.magasins" class="magasin-card mdl-card mdl-shadow--2dp">
            <div class="mdl-card__title">
              <h2 class="mdl-card__title-text">{{ magasin.enseigne }} - {{ magasin.site }}</h2>
            </div>
            <div class="mdl-card__supporting-text">Date d'ajout : {{ magasin.dateajout }}</div>
            <div class="mdl-card__actions mdl-card--border" @click="afficherDetails(magasin.id)">
              Détails
            </div>
            <div class="mdl-card__menu">
              <button class="mdl-button mdl-button--icon mdl-js-button mdl-js-ripple-effect" @click="sendMail(magasin.id)">
                <i class="material-icons">share</i>
              </button>
            </div>
          </div>
        </div>
      </div>
      <div v-if="this.$cookie.get('idUtilisateur')">
        <router-link class="ajouter-magasin-button mdl-button mdl-js-button mdl-button--fab mdl-button--colored" to="/ajout">
          <i class="material-icons">add</i>
        </router-link>
      </div>
    </div>
  </div>
  <div v-else>
    <div class="actions">
      <a href="/" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
        Connectez-vous
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      magasins: '',
      'msg': ''
    }
  },
  methods: {
    afficherDetails (id) {
      this.$router.push({name: 'detail', params: { id: id }})
    },
    listeMagasins () {
      if (navigator.onLine) {
        this.$http.get('http://10.110.24.121:80/CFGRest/public/magasins/' + this.$cookie.get('idUtilisateur'))
          .then(response => {
            this.magasins = response.body
            localStorage.setItem('magasins', JSON.stringify(response.body))
          })
      } else {
        this.magasins = JSON.parse(localStorage.getItem('magasins'))
      }
    },
    sendMail (id) {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/mail/' + id)
      this.$swal('Envoyé !', 'Mail envoyé.', 'success')
    }
  },
  mounted () {
    this.listeMagasins()
  }
}
</script>

<style scoped>
  .ajouter-magasin-button {
    position: fixed;
    right: 24px;
    bottom: 24px;
    z-index: 998;
  }
  .magasin-card {
    color: #fff;
    float: left; 
    height: auto;
    min-height: 40px;
    width: 22%;
    margin: 5px;
    background-color: rgb(0,134,89);
    text-align: center;
  }
  .magasin-card > .mdl-card__title {
    color: #fff;
  }
  .magasin-card > .mdl-card__supporting-text {
    color: #fff;
  }
  .magasin-card > .mdl-card__actions {
    background-color: #fff;
    color: rgb(0,134,89);
  }
  .magasin-card > .mdl-card__actions:hover {
    background-color: rgb(0,134,89);
    color: #fff;
    cursor:pointer;
  }

  @media screen and (max-width: 700px) {
    .magasin-card {
      color: #fff;
      float: left; 
      height: auto;
      width: 100%;
      margin-right: 1px;
      padding: 10px 0;
      background-color: rgb(0,134,89);
      text-align: center;
    }
  }

  .actions {
    text-align: center;
    margin-top: 10px;
  }

  .actions > a {
    text-align: center;
    background-color: rgb(0,134,89);
  }

  .actions > a:hover {
    background-color: rgb(0,134,39);
  }
</style>