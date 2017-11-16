<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <form>
      <div class="mdl-grid">
        <div v-for="equipement in this.equipements">
          <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="designation" v-model="designation = equipement.designation" type="text" class="mdl-textfield__input" />
              <label for="designation" class="mdl-textfield__label">Désignation</label>
            </div>
            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input id="reference" v-model="reference = equipement.reference" type="text" class="mdl-textfield__input"/>
              <label for="reference" class="mdl-textfield__label">Référence</label>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <div v-if="type === 'logiciels'">
                <input id="licence" v-model="licence = equipement.licence" type="text" class="mdl-textfield__input"/>
                <label for="licence" class="mdl-textfield__label">Licence</label>
              </div>
              <div v-else>
                <input id="numeroserie" v-model="numeroserie = equipement.numeroserie" type="text" class="mdl-textfield__input"/>
                <label for="numeroserie" class="mdl-textfield__label">Numéro de série</label>
              </div>
            </div>

            <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
              <input class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="nombre" v-model="quantite = equipement.quantite">
              <label for="quantite" class="mdl-textfield__label">Quantité</label>
              <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
            </div>

            <div class="actions">
              <a @click.prevent="modifEquipement" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Modifier l'équipement
              </a>
              <a @click.prevent="suppEquipement" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                Supprimer l'équipement
              </a>
              <a @click.prevent="listeEquipement" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
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
      equipements: '',
      'designation': '',
      'reference': '',
      'numeroserie': '',
      'licence': '',
      'quantite': '',
      'type': this.$route.params.type
    }
  },
  methods: {
    detailsEquipement () {
      if (this.type === 'serveurs') {
        this.$http.get('http://10.110.24.121:80/CFGRest/public/serveur/' + this.$route.params.id)
        .then(response => {
          this.equipements = response.body
        })
      }
      if (this.type === 'tpv') {
        this.$http.get('http://10.110.24.121:80/CFGRest/public/tpv/' + this.$route.params.id)
        .then(response => {
          this.equipements = response.body
        })
      }
      if (this.type === 'logiciels') {
        this.$http.get('http://10.110.24.121:80/CFGRest/public/logiciel/' + this.$route.params.id)
        .then(response => {
          this.equipements = response.body
        })
      }
    },
    modifEquipement () {
      if (this.type === 'serveurs') {
        this.$http.put('http://10.110.24.121:80/CFGRest/public/serveur/' + this.$route.params.id, {
          'designation': this.designation,
          'reference': this.reference,
          'numeroserie': this.numeroserie,
          'quantite': this.quantite
        }, {emulateJSON: true})
        this.$swal('Modifié !', 'Le serveur a été modifié.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
      if (this.type === 'tpv') {
        this.$http.put('http://10.110.24.121:80/CFGRest/public/tpv/' + this.$route.params.id, {
          'designation': this.designation,
          'reference': this.reference,
          'numeroserie': this.numeroserie,
          'quantite': this.quantite
        }, {emulateJSON: true})
        this.$swal('Modifié !', 'Le TPV a été modifié.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
      if (this.type === 'logiciels') {
        this.$http.put('http://10.110.24.121:80/CFGRest/public/logiciel/' + this.$route.params.id, {
          'designation': this.designation,
          'reference': this.reference,
          'licence': this.licence,
          'quantite': this.quantite
        }, {emulateJSON: true})
        this.$swal('Modifié !', 'Le logiciel a été modifié.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
    },
    suppEquipement () {
      if (this.type === 'serveurs') {
        this.$http.delete('http://10.110.24.121:80/CFGRest/public/serveur/' + this.$route.params.id)
        this.$swal('Supprimé !', 'Le magasin a été supprimé.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
      if (this.type === 'tpv') {
        this.$http.delete('http://10.110.24.121:80/CFGRest/public/tpv/' + this.$route.params.id)
        this.$swal('Supprimé !', 'Le magasin a été supprimé.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
      if (this.type === 'logiciels') {
        this.$http.delete('http://10.110.24.121:80/CFGRest/public/logiciel/' + this.$route.params.id)
        this.$swal('Supprimé !', 'Le magasin a été supprimé.', 'success')
        .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
      }
    },
    listeEquipement () {
      this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }})
    }
  },
  created () {
    this.detailsEquipement()
  }
}
</script>

<style scoped>
  form {
    text-align: center;
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
</style>