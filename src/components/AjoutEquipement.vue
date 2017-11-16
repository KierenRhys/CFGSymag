<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <vue-tabs centered
              active-tab-color="white"
              active-text-color="rgb(0,134,89)"
    >
      <v-tab title="Serveur" icon="mdl-router">
        <form>
          <div class="mdl-grid">
            <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="designation" v-model="designation" type="text" class="mdl-textfield__input"/>
                <label for="designation" class="mdl-textfield__label">Désignation</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="reference" v-model="reference" type="text" class="mdl-textfield__input"/>
                <label for="reference" class="mdl-textfield__label">Référence</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="numeroserie" v-model="numeroserie" type="text" class="mdl-textfield__input"/>
                <label for="numeroserie" class="mdl-textfield__label">Numéro de série</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input v-model="quantite" class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="quantite">
                <label class="mdl-textfield__label" for="quantite">Quantité</label>
                <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
              </div>

              <div class="actions">
                <a @click.prevent="ajoutServeur" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                  Ajouter un serveur
                </a>
              </div>
            </div>
          </div>
        </form>
      </v-tab>

      <v-tab title="TPV">
        <form>
          <div class="mdl-grid">
            <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="designation" v-model="designation" type="text" class="mdl-textfield__input"/>
                <label for="designation" class="mdl-textfield__label">Désignation</label>
              </div>
              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="reference" v-model="reference" type="text" class="mdl-textfield__input"/>
                <label for="reference" class="mdl-textfield__label">Référence</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="numeroserie" v-model="numeroserie" type="text" class="mdl-textfield__input"/>
                <label for="numeroserie" class="mdl-textfield__label">Numéro de série</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input v-model="quantite" class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="quantite">
                <label class="mdl-textfield__label" for="quantite">Quantité</label>
                <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
              </div>
              <div class="actions">
                <a @click.prevent="ajoutTPV" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                  Ajouter un TPV
                </a>
              </div>
            </div>
          </div>
        </form>
      </v-tab>

      <v-tab title="Logiciel">
        <form>
          <div class="mdl-grid">
            <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="designation" v-model="designation" type="text" class="mdl-textfield__input"/>
                <label for="designation" class="mdl-textfield__label">Désignation</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="reference" v-model="reference" type="text" class="mdl-textfield__input"/>
                <label for="reference" class="mdl-textfield__label">Référence</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="licence" v-model="licence" type="text" class="mdl-textfield__input"/>
                <label for="licence" class="mdl-textfield__label">Licence</label>
              </div>

              <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
                <input id="quantite" v-model="quantite"  class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?">
                <label class="mdl-textfield__label" for="quantite">Quantité</label>
                <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
              </div>
              <div class="actions">
                <a @click.prevent="ajoutLogiciel" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
                  Ajouter un logiciel
                </a>
              </div>
            </div>
          </div>
        </form>
      </v-tab>
    </vue-tabs>
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
      'designation': '',
      'reference': '',
      'numeroserie': '',
      'licence': '',
      'quantite': ''
    }
  },
  methods: {
    ajoutServeur () {
      this.$http.post('http://10.110.24.121:80/CFGRest/public/serveur', {
        'designation': this.designation,
        'reference': this.reference,
        'numeroserie': this.numeroserie,
        'quantite': this.quantite,
        'idmagasin': this.$cookie.get('idMag')
      }, {emulateJSON: true})
      this.$swal('Ajouté !', 'Le serveur a été ajouté.', 'success')
      .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
    },
    ajoutTPV () {
      this.$http.post('http://10.110.24.121:80/CFGRest/public/tpv', {
        'designation': this.designation,
        'reference': this.reference,
        'numeroserie': this.numeroserie,
        'quantite': this.quantite,
        'idmagasin': this.$cookie.get('idMag')
      }, {emulateJSON: true})
      this.$swal('Ajouté !', 'Le tpv a été ajouté.', 'success')
      .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
    },
    ajoutLogiciel () {
      this.$http.post('http://10.110.24.121:80/CFGRest/public/logiciel', {
        'designation': this.designation,
        'reference': this.reference,
        'licence': this.numeroserie,
        'quantite': this.quantite,
        'idmagasin': this.$cookie.get('idMag')
      }, {emulateJSON: true})
      this.$swal('Ajouté !', 'Le logiciel a été ajouté.', 'success')
      .then(this.$router.push({name: 'equipements', params: { id: this.$cookie.get('idMag') }}))
    }
  }
}
</script>

<style scoped>
  .waiting {
    padding: 10px;
    color: #555;
  }
  h1 {
    text-align: center;
    color: rgb(0,134,89);
  }
  form {
    text-align: center;
  }
  title {
    font-weight: bold;
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