<template>
  <div v-if="this.$cookie.get('idUtilisateur')">
    <form>
      <div class="mdl-grid">
        <div class="mdl-cell mdl-cell--12-col mdl-cell--8-col-tablet">
          <h2>Informations</h2>
          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="enseigne" v-model="enseigne" type="text" class="mdl-textfield__input"/>
            <label for="enseigne" class="mdl-textfield__label">Enseigne</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="site" v-model="site" type="text" class="mdl-textfield__input"/>
            <label for="site" class="mdl-textfield__label">Site</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="adresse" v-model="adresse" type="text" class="mdl-textfield__input"/>
            <label for="adresse" class="mdl-textfield__label">Adresse</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="ville" v-model="ville" type="text" class="mdl-textfield__input"/>
            <label for="ville" class="mdl-textfield__label">Ville</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="CP" v-model="CP" type="text" class="mdl-textfield__input"/>
            <label for="CP" class="mdl-textfield__label">CP</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="responsable" v-model="responsable" type="text" class="mdl-textfield__input"/>
            <label for="responsable" class="mdl-textfield__label">Responsable</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="telephone" v-model="telephone" type="text" class="mdl-textfield__input"/>
            <label for="telephone" class="mdl-textfield__label">Telephone</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="contact" v-model="contact" type="text" class="mdl-textfield__input"/>
            <label for="contact" class="mdl-textfield__label">Contact</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="fax" v-model="fax" type="text" class="mdl-textfield__input"/>
            <label for="fax" class="mdl-textfield__label">Fax</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="caisses" v-model="caisses" type="text" class="mdl-textfield__input"/>
            <label for="caisses" class="mdl-textfield__label">Caisses</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="nombre" v-model="nombre">
            <label for="nombre" class="mdl-textfield__label">Nombre</label>
            <span class="mdl-textfield__error">Veuillez renseigner un nombre !</span>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <input id="telemaintenance" v-model="telemaintenance" type="text" class="mdl-textfield__input"/>
            <label for="telemaintenance" class="mdl-textfield__label">Telemaintenance</label>
          </div>

          <h2>Horaires</h2>
          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <!-- <label class="mdl-switch mdl-js-switch mdl-js-ripple-effect" for="checkboxLundi">
              <input type="checkbox" id="checkboxLundi" v-model="ouvertureLundi" class="mdl-switch__input">
              <span class="mdl-switch__label">Ouvert</span>
            </label> -->
            <switches class="switches" v-model="ouvertureLundi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureLundi == true">
              <select v-model="lundiDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="lundiDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="lundiFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="lundiFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="lundiDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Lundi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureMardi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureMardi== true">
              <select v-model="mardiDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="mardiDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="mardiFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="mardiFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="mardiDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Mardi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureMercredi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureMercredi== true">
              <select v-model="mercrediDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="mercrediDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="mercrediFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="mercrediFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="mercrediDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Mercredi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureJeudi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureJeudi== true">
              <select v-model="jeudiDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="jeudiDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="jeudiFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="jeudiFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="jeudiDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Jeudi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureVendredi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureVendredi== true">
              <select v-model="vendrediDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="vendrediDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="vendrediFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="vendrediFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="vendrediDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Vendredi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureSamedi" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureSamedi== true">
              <select v-model="samediDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="samediDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="samediFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="samediFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="samediDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Samedi</label>
          </div>

          <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label is-upgrated is-dirty">
            <switches class="switches" v-model="ouvertureDimanche" theme="bootstrap" text-enabled="Ouverture" text-disabled="Fermeture" color="success"></switches>
            <div v-if="ouvertureDimanche== true">
              <select v-model="dimancheDebutH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="dimancheDebutM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
              /
              <select v-model="dimancheFinH">
                <option disabled value="">hh</option>
                <option>00</option>
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
                <option>21</option>
                <option>22</option>
                <option>23</option>
              </select>
              :
              <select v-model="dimancheFinM">
                <option disabled value="">mm</option>
                <option>00</option>
                <option>15</option>
                <option>30</option>
                <option>45</option>
              </select>
            </div>
            <div v-else>
              <select v-model="dimancheDebutH" disabled>
                <option disabled value="">fermé</option>
              </select>
            </div>
            <label class="mdl-textfield__label">Dimanche</label>
          </div>

          <div class="actions">
            <a @click.prevent="ajoutMagasin" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
              Ajouter un magasin
            </a>
            <a href="/" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">
              Retour
            </a>
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
import Switches from 'vue-switches'
export default {
  components: {
    Switches
  },
  data () {
    return {
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
      'nombre': '',
      'telemaintenance': '',

      'ouvertureLundi': true,
      'ouvertureMardi': true,
      'ouvertureMercredi': true,
      'ouvertureJeudi': true,
      'ouvertureVendredi': true,
      'ouvertureSamedi': true,
      'ouvertureDimanche': true,
      'lundiDebutH': '',
      'lundiDebutM': '',
      'lundiFinH': '',
      'lundiFinM': '',
      'mardiDebutH': '',
      'mardiDebutM': '',
      'mardiFinH': '',
      'mardiFinM': '',
      'mercrediDebutH': '',
      'mercrediDebutM': '',
      'mercrediFinH': '',
      'mercrediFinM': '',
      'jeudiDebutH': '',
      'jeudiDebutM': '',
      'jeudiFinH': '',
      'jeudiFinM': '',
      'vendrediDebutH': '',
      'vendrediDebutM': '',
      'vendrediFinH': '',
      'vendrediFinM': '',
      'samediDebutH': '',
      'samediDebutM': '',
      'samediFinH': '',
      'samediFinM': '',
      'dimancheDebutH': '',
      'dimancheDebutM': '',
      'dimancheFinH': '',
      'dimancheFinM': ''
    }
  },
  methods: {
    ajoutMagasin () {
      var lundiDebut = 'fermé'
      var lundiFin = 'fermé'
      var mardiDebut = 'fermé'
      var mardiFin = 'fermé'
      var mercrediDebut = 'fermé'
      var mercrediFin = 'fermé'
      var jeudiDebut = 'fermé'
      var jeudiFin = 'fermé'
      var vendrediDebut = 'fermé'
      var vendrediFin = 'fermé'
      var samediDebut = 'fermé'
      var samediFin = 'fermé'
      var dimancheDebut = 'fermé'
      var dimancheFin = 'fermé'
      if (this.ouvertureLundi === true) {
        lundiDebut = this.lundiDebutH + ':' + this.lundiDebutM
        lundiFin = this.lundiFinH + ':' + this.lundiFinM
      }
      if (this.ouvertureMardi === true) {
        mardiDebut = this.mardiDebutH + ':' + this.mardiDebutM
        mardiFin = this.mardiFinH + ':' + this.mardiFinM
      }
      if (this.ouvertureMercredi === true) {
        mercrediDebut = this.mercrediDebutH + ':' + this.mercrediDebutM
        mercrediFin = this.mercrediFinH + ':' + this.mercrediFinM
      }
      if (this.ouvertureJeudi === true) {
        jeudiDebut = this.jeudiDebutH + ':' + this.jeudiDebutM
        jeudiFin = this.jeudiFinH + ':' + this.jeudiFinM
      }
      if (this.ouvertureVendredi === true) {
        vendrediDebut = this.vendrediDebutH + ':' + this.vendrediDebutM
        vendrediFin = this.vendrediFinH + ':' + this.vendrediFinM
      }
      if (this.ouvertureSamedi === true) {
        samediDebut = this.samediDebutH + ':' + this.samediDebutM
        samediFin = this.samediFinH + ':' + this.samediFinM
      }
      if (this.ouvertureDimanche === true) {
        dimancheDebut = this.dimancheDebutH + ':' + this.dimancheDebutM
        dimancheFin = this.dimancheFinH + ':' + this.dimancheFinM
      }
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
      this.$http.post('http://10.110.24.121:80/CFGRest/public/magasin', {
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
        'idutilisateur': this.$cookie.get('idUtilisateur'),
        'lundiDebut': lundiDebut,
        'lundiFin': lundiFin,
        'mardiDebut': mardiDebut,
        'mardiFin': mardiFin,
        'mercrediDebut': mercrediDebut,
        'mercrediFin': mercrediFin,
        'jeudiDebut': jeudiDebut,
        'jeudiFin': jeudiFin,
        'vendrediDebut': vendrediDebut,
        'vendrediFin': vendrediFin,
        'samediDebut': samediDebut,
        'samediFin': samediFin,
        'dimancheDebut': dimancheDebut,
        'dimancheFin': dimancheFin
      }, {emulateJSON: true})
      this.$swal('Ajouté !', 'Le magasin a été ajouté.', 'success')
      .then(this.$router.push('/'))
    }
  }
}
</script>

<style scoped>
  .waiting {
    padding: 10px;
    color: #555;
  }
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
    background-color: rgb(0,134,89);
  }

  .actions > a:hover {
    background-color: rgb(0,134,39);
  }

  .switches {
    margin: 25px;
  }
</style>