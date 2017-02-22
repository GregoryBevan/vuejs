<template lang="html">
  <div>
    <label for="pieces-jointes">Pièces jointes</label>
    <dropzone id="pieces-jointes" url="none" :autoProcessQueue="false" :useFontAwesome="true" :acceptedFileTypes="'application/pdf'" :language="language" v-on:vdropzone-file-added="fileAdded"></dropzone>
  </div>
</template>

<script>
import Dropzone from 'vue2-dropzone'

export default {
  name: 'pieces-jointes',
  data: function() {
    return {
      language: {
        dictDefaultMessage: '<div>Déposer les pièces jointes</div>',
        dictRemoveFile: 'Supprimer'
      }
    }
  },
  components: {
    Dropzone
  },
  methods: {
    'fileAdded': function(file) {
      console.log("The " + file + "has been added")
    }
  }
}
</script>

<style lang="css">
</style>
