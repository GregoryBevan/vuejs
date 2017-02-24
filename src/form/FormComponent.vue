<template lang="html">
  <div class="container">
    <div class="row col-xs-12">
      <form ref="mainForm">
        <div class="form-group col-xs-6">
          <label for="societe">Société</label>
          <select id="societe" v-model="societe" class="form-control">
            <option disabled value=""> -- Sélectionner -- </option>
            <option value="4" title="4">CBP France</option>
            <option value="11" title="11">CBP Italia</option>
            <option value="12" title="12">CBP Protection de Pagos</option>
            <option value="13" title="13">CBP DE</option>
          </select>
        </div>
        <div class="form-group col-xs-6">
          <label for="domaine">Domaine</label>
          <select id="domaine" v-model="domaine" class="form-control">
            <option disabled value=""> -- Sélectionner -- </option>
            <option value="1" title="1">Adhésion</option>
            <option value="2" title="2">Sinistre</option>
            <option value="3" title="3">SR</option>
          </select>
        </div>
        <div class="form-group col-xs-12">
          <piece-principale></piece-principale>
        </div>
        <div class="form-group col-xs-12">
          <pieces-jointes></pieces-jointes>
        </div>
      </div>
      <div class="form-group col-xs-12">
        <p class=" text-center">
          <input type="submit" class="btn btn-primary" value="Envoyer" @click="submitForm">
        </p>
      </div>
    </form>
  </div>
</template>

<script>
import PiecePrincipale from './pieceprincipale/PiecePrincipale.vue'
import PiecesJointes from './piecesjointes/PiecesJointes.vue'
import {EventBus} from '../bus.js'

export default {
  name: 'form-component',
  data: () => ({
    societe: "",
    domaine: "",
    piecePrincipaleFile: {}
  }),
  components: {
    PiecePrincipale,
    PiecesJointes
  },
  mounted() {
    EventBus.$on('piecePrincipaleUpdated', file => {
      console.log("File to uplaod :");
      console.log(file);
      this.piecePrincipaleFile=file;
    });
  },
  methods: {
    'submitForm': function(event) {
      event.preventDefault();
      console.log(this.piecePrincipaleFile);
      var formData = this.getFormData();
      this.$http.post('api/', formData).then((response) => {
        console.log('trop cool');
      }, (response) => {
        console.log('Putain ça marche pas');
      })
    },
    'piecePrincipaleUpdate': function(file) {
      console.log("Update piece principale");
    },
    'getFormData': function() {
      var formData = new FormData();
      formData.append('societe', this.societe);
      formData.append('domaine', this.domaine);
      formData.append('type-reception', 7);
      formData.append('idCheminRelatif', 147);
      formData.append('etat', 12);
      formData.append('file', this.piecePrincipaleFile, this.piecePrincipaleFile.name);
      return formData;
    }
  }
}
</script>

<style lang="scss">
select option:first-child {
  font-style: italic;
}
</style>
