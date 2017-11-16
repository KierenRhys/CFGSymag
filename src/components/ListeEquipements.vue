<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <div>
      <div class="mdl-grid">
        <!-- <div class="mdl-cell mdl-cell--3-col mdl-cell mdl-cell--1-col-tablet mdl-cell--hide-phone"></div> -->
        <div class="mdl-cell mdl-cell--12-col mdl-cell--12-col-phone">
          <vue-tabs centered
                    active-tab-color="white"
                    active-text-color="rgb(0,134,89)">
            <v-tab title="Serveur">
              <div v-for="serveur in this.serveurs" class="equipement-card" @click="afficherDetailsServeur(serveur.id, 'serveurs')">
                <span class="equipement-card__nom">{{ serveur.designation }} - {{ serveur.reference }}</span>
              </div>
            </v-tab>

            <v-tab title="TPV">
              <div v-for="tpv in this.tpvs" class="equipement-card" @click="afficherDetailsTpv(tpv.id, 'tpv')">
                <span class="equipement-card__nom">{{ tpv.designation }} - {{ tpv.reference }}</span>
              </div>
            </v-tab>

            <v-tab title="Logiciel">
              <div v-for="logiciel in this.logiciels" class="equipement-card" @click="afficherDetailsLogiciel(logiciel.id, 'logiciels')">
                <span class="equipement-card__nom">{{ logiciel.designation }} - {{ logiciel.reference }}</span>
              </div>
            </v-tab>
          </vue-tabs>
        </div>
      </div>
      <div v-if="this.$cookie.get('idUtilisateur')">
        <router-link class="ajouter-equipement-button mdl-button mdl-js-button mdl-button--fab mdl-button--colored" to="/ajoutEquip">
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
      serveurs: '',
      logiciels: '',
      tpvs: ''
    }
  },
  methods: {
    listeServeurs () {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/magasin/serveurs/' + this.$route.params.id)
      .then(response => {
        this.serveurs = response.body
      })
    },
    listeLogiciels () {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/magasin/logiciels/' + this.$route.params.id)
      .then(response => {
        this.logiciels = response.body
      })
    },
    listeTpvs () {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/magasin/tpvs/' + this.$route.params.id)
      .then(response => {
        this.tpvs = response.body
      })
    },
    afficherDetailsServeur (id, type) {
      this.$router.push({name: 'detailsEquip', params: { id: id, type: type }})
    },
    afficherDetailsTpv (id, type) {
      this.$router.push({name: 'detailsEquip', params: { id: id, type: type }})
    },
    afficherDetailsLogiciel (id, type) {
      this.$router.push({name: 'detailsEquip', params: { id: id, type: type }})
    }
  },
  mounted () {
    this.listeServeurs()
    this.listeLogiciels()
    this.listeTpvs()
    this.$cookie.set('idMag', this.$route.params.id, 1)
  }
}
</script>

<style scoped>
  .ajouter-equipement-button {
    position: fixed;
    right: 24px;
    bottom: 24px;
    z-index: 998;
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
  .equipement-card {
    color: #fff;
    float: left; 
    height: auto;
    min-height: 40px;
    width: 22%;
    margin: 5px;
    padding: 20px 0;
    background-color: rgb(0,134,89);
    text-align: center;
  }
  .equipement-card:hover{
    background-color: rgb(0,134,39);
  }
  .equipement-card > span {
    float: center;
  }
  .equipement-card__nom {
    font-weight: bold;
  }

  @media screen and (max-width: 700px) {
    .equipement-card {
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
</style>