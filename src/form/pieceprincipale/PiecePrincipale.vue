<template lang="html">
  <div>
    <label>Pièce principale</label>
    <div class="input-group">
      <label class="input-group-btn">
        <span class="btn btn-primary">
          Parcourir&hellip; <input type="file" style="display: none;" @change="setPiecePrincipalePath">
        </span>
      </label>
      <input type="text" id="piece-principale" ref="piecePrincipale" class="form-control" readonly>
    </div>
  </div>
</template>

<script>

export default {
  name: 'piece-principale',
  data() {
    return {
      file: ''
    }
  },
  methods: {
    setPiecePrincipalePath(event) {
      this.$refs.piecePrincipale.value=event.srcElement.value;
    }
  }
}
</script>

<style lang="scss">
.btn-primary {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:hover {
  background-color: #286090;
  border-color: #204d74;
}
</style>
