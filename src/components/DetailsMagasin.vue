<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <form>
      <div class="mdl-grid">
        <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
          <div v-for="magasin in this.magasins">
            <h2>Informations</h2>
            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="enseigne" v-model="enseigne = magasin.enseigne" type="text" class="mdl-textfield__input" />
              <label for="enseigne" class="mdl-textfield__label">Enseigne</label>
            </div>
            
            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="site" v-model="site = magasin.site" type="text" class="mdl-textfield__input"/>
              <label for="site" class="mdl-textfield__label">Site</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="adresse" v-model="adresse = magasin.adresse" type="text" class="mdl-textfield__input"/>
              <label for="adresse" class="mdl-textfield__label">Adresse</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="ville" v-model="ville = magasin.ville" type="text" class="mdl-textfield__input"/>
              <label for="ville" class="mdl-textfield__label">Ville</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="CP" v-model="CP = magasin.CP" type="text" class="mdl-textfield__input"/>
              <label for="CP" class="mdl-textfield__label">CP</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="responsable" v-model="responsable = magasin.responsable" type="text" class="mdl-textfield__input"/>
              <label for="responsable" class="mdl-textfield__label">Responsable</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="telephone" v-model="telephone = magasin.telephone" type="text" class="mdl-textfield__input"/>
              <label for="telephone" class="mdl-textfield__label">Telephone</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="contact" v-model="contact = magasin.contact" type="text" class="mdl-textfield__input"/>
              <label for="contact" class="mdl-textfield__label">Contact</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="fax" v-model="fax = magasin.fax" type="text" class="mdl-textfield__input"/>
              <label for="fax" class="mdl-textfield__label">Fax</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="caisses" v-model="caisses = magasin.caisses" type="text" class="mdl-textfield__input"/>
              <label for="caisses" class="mdl-textfield__label">Caisses</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="nombre" v-model="nombre = magasin.nombre">
              <label for="nombre" class="mdl-textfield__label">Nombre</label>
              <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="telemaintenance" v-model="telemaintenance = magasin.telemaintenance" type="text" class="mdl-textfield__input"/>
              <label for="telemaintenance" class="mdl-textfield__label">Telemaintenance</label>
            </div>

            <h2>Horaires</h2>
            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="lundiDebut" v-model="lundiDebut = magasin.lundiDebut" type="time" class="mdl-textfield__input"/>
              <input id="lundiFin" v-model="lundiFin = magasin.lundiFin" type="time" class="mdl-textfield__input"/>
              <label for="lundiDebut" class="mdl-textfield__label">Lundi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="mardiDebut" v-model="mardiDebut = magasin.mardiDebut" type="time" class="mdl-textfield__input"/>
              <input id="mardiFin" v-model="mardiFin = magasin.mardiFin" type="time" class="mdl-textfield__input"/>
              <label for="mardiDebut" class="mdl-textfield__label">Mardi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="mercrediDebut" v-model="mercrediDebut = magasin.mercrediDebut" type="time" class="mdl-textfield__input"/>
              <input id="mercrediFin" v-model="mercrediFin = magasin.mercrediFin" type="time" class="mdl-textfield__input"/>
              <label for="mercrediDebut" class="mdl-textfield__label">Mercredi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="jeudiDebut" v-model="jeudiDebut = magasin.jeudiDebut" type="time" class="mdl-textfield__input"/>
              <input id="jeudiFin" v-model="jeudiFin = magasin.jeudiFin" type="time" class="mdl-textfield__input"/>
              <label for="jeudiDebut" class="mdl-textfield__label">Jeudi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="vendrediDebut" v-model="vendrediDebut = magasin.vendrediDebut" type="time" class="mdl-textfield__input"/>
              <input id="vendrediFin" v-model="vendrediFin = magasin.vendrediFin" type="time" class="mdl-textfield__input"/>
              <label for="vendrediDebut" class="mdl-textfield__label">Vendredi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="samediDebut" v-model="samediDebut = magasin.samediDebut" type="time" class="mdl-textfield__input"/>
              <input id="samediFin" v-model="samediFin = magasin.samediFin" type="time" class="mdl-textfield__input"/>
              <label for="samediDebut" class="mdl-textfield__label">Samedi</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="dimancheDebut" v-model="dimancheDebut = magasin.dimancheDebut" type="time" class="mdl-textfield__input"/>
              <input id="dimancheFin" v-model="dimancheFin = magasin.dimancheFin" type="time" class="mdl-textfield__input"/>
              <label for="dimancheDebut" class="mdl-textfield__label">Dimanche</label>
            </div>
            <div class="actions">
              <a @click.prevent="modifMagasin" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Modifier le magasin
              </a>
              <a @click="listeEquipements(magasin.id)" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Voir les équipements
              </a>
              <a @click.prevent="suppMagasin" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Supprimer le magasin
              </a>
              <a @click.prevent="listeMagasin" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Retour
              </a>
            </div>
          </div>
        </div>
      </div>
    </form>
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
      'dateajout': '',
      'enseigne': '',
      'site': '',
      'adresse': '',
      'ville': '',
      'CP': '',
      'responsable': '',
      'telephone': '',
      'contact': '',
      'fax': '',
      'caisses': '',
      'nombre': 0,
      'telemaintenance': '',
      'lundiDebut': null,
      'lundiFin': null,
      'mardiDebut': null,
      'mardiFin': null,
      'mercrediDebut': null,
      'mercrediFin': null,
      'jeudiDebut': null,
      'jeudiFin': null,
      'vendrediDebut': null,
      'vendrediFin': null,
      'samediDebut': null,
      'samediFin': null,
      'dimancheDebut': null,
      'dimancheFin': null
    }
  },
  methods: {
    detailsMagasins () {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/magasin/' + this.$route.params.id)
      .then(response => {
        this.magasins = response.body
      })
    },
    modifMagasin () {
      var date = new Date()
      var dd = date.getDate()
      var mm = date.getMonth() + 1
      var yyyy = date.getFullYear()
      var hour = date.getHours()
      var minu = date.getMinutes()
      var sec = date.getSeconds()
      if (dd < 10) { dd = '0' + dd }
      if (mm < 10) { mm = '0' + mm }
      if (minu < 10) { minu = '0' + minu }
      date = yyyy + '-' + mm + '-' + dd + ' ' + hour + ':' + minu + ':' + sec
      this.$http.put('http://10.110.24.121:80/CFGRest/public/magasin/' + this.$route.params.id, {
        'dateajout': date,
        'enseigne': this.enseigne,
        'site': this.site,
        'adresse': this.adresse,
        'ville': this.ville,
        'CP': this.CP,
        'responsable': this.responsable,
        'telephone': this.telephone,
        'contact': this.contact,
        'fax': this.fax,
        'caisses': this.caisses,
        'nombre': this.nombre,
        'telemaintenance': this.telemaintenance,
        'lundiDebut': this.lundiDebut,
        'lundiFin': this.lundiFin,
        'mardiDebut': this.mardiDebut,
        'mardiFin': this.mardiFin,
        'mercrediDebut': this.mercrediDebut,
        'mercrediFin': this.mercrediFin,
        'jeudiDebut': this.jeudiDebut,
        'jeudiFin': this.jeudiFin,
        'vendrediDebut': this.vendrediDebut,
        'vendrediFin': this.vendrediFin,
        'samediDebut': this.samediDebut,
        'samediFin': this.samediFin,
        'dimancheDebut': this.dimancheDebut,
        'dimancheFin': this.dimancheFin
      }, {emulateJSON: true})
      this.$swal('Modifié !', 'Le magasin a été modifié.', 'success')
      .then(this.$router.push('/magasin/' + this.$route.params.id))
    },
    suppMagasin () {
      this.$http.delete('http://10.110.24.121:80/CFGRest/public/magasin/' + this.$route.params.id)
      this.$swal('Supprimé !', 'Le magasin a été supprimé.', 'success')
      .then(this.$router.push('/'))
    },
    listeEquipements (id) {
      this.$router.push({name: 'equipements', params: { id: id }})
    },
    listeMagasin () {
      this.$router.push('/')
    }
  },
  created () {
    this.detailsMagasins()
  }
}
</script>

<style scoped>
  form {
    text-align: center;
  }
  h2 {
    color: rgb(0,134,89);
  }
  .actions {
    text-align: center;
    margin-top: 10px;
  }
  .actions > a {
    text-align: center;
    margin-bottom: 5px;
    background-color: rgb(0,134,89);
  }

  .actions > a:hover {
    background-color: rgb(0,134,39);
  }

  #share {
    color: rgb(0,134,89)
  }
</style>