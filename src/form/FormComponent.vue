<template lang="html">
  <div class="container">
    <div class="row col-xs-12">
      <form ref="main-form" id="main-form">
        <div class="form-group col-xs-6">
          <label for="societe">Société</label>
          <select id="societe" name="societe" class="form-control">
            <option disabled selected value> -- Sélectionner -- </option>
            <option value="4" title="4">CBP France</option>
            <option value="11" title="11">CBP Italia</option>
            <option value="12" title="12">CBP Protection de Pagos</option>
            <option value="13" title="13">CBP DE</option>
          </select>
        </div>
        <div class="form-group col-xs-6">
          <label for="domaine">Domaine</label>
          <select id="domaine" name="domaine" class="form-control">
            <option disabled selected value> -- Sélectionner -- </option>
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
      <input type="hidden" name="type-reception" value="7">
      <input type="hidden" name="idCheminRelatif" value="147">
      <input type="hidden" name="etat" value="12">
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
  data() {
	  return {
		  piecePrincipaleFile: {}
	  }
  },
  components: {
    PiecePrincipale,
    PiecesJointes
  },
  created() {
	  EventBus.$on('piecePrincipaleUpdated', function(file) {
		 console.log(file);
	})
  },
  methods: {
    'submitForm': function() {
    	var formData = new FormData();
    	formData.append('file', 'bar');
    	this.$http.post('api/', formData).then((response) => {
    		console.log('trop cool');
    	}, (response) => {
    		console.log('Putain ça marche pas');
    	})
    	this.$http.get('api/').then((response) => {
            console.log('test')
        }, (response) => {
            // error callback
        });
    },
    'piecePrincipaleUpdate': function(file) {
    	console.log("Update piece principale");
    }
  }
}
</script>

<style lang="scss">
select option:first-child {
  font-style: italic;
}
</style>
