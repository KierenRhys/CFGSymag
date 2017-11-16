<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <div class="actions">
      <a href="/" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
        (Connecté-e) Voir les magasins
      </a>
    </div>
  </div>
  <div v-else>
    <form>
      <div class="mdl-grid">
        <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="login" v-model="login" type="text" class="mdl-textfield__input" />
            <label for="login" class="mdl-textfield__label">Login</label>
          </div>
          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="password" v-model="password" type="password" class="mdl-textfield__input" />
            <label for="password" class="mdl-textfield__label">Password</label>
          </div>
          <div class="actions">
            <a @click.prevent="connexion" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
              Se connecter
            </a>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
var sha512 = require('js-sha512')
export default {
  data () {
    return {
      'login': '',
      'password': '',
      idUtilisateur: ''
    }
  },
  methods: {
    connexion () {
      this.$http.get('http://10.110.24.121:80/CFGRest/public/utilisateur/' + this.login + '/' + sha512(this.password))
      .then(response => {
        this.idUtilisateur = response.body
        this.$cookie.set('idUtilisateur', this.idUtilisateur, 1)
        this.$router.push('/')
      })
    }
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
    background-color: rgb(0,134,89);
  }
</style>