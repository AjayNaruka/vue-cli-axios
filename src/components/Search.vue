<template>
  <form class="d-flex">
    <div class="flex-grow-1">
      <input
        class="form-control"
        placeholder="Cerca"
        v-model.trim=searchText
        type="text">
    </div>
    <div>
      <button class="ms-3 btn btn-primary" @click.prevent="startSearch()">CERCA</button> <!-- PREVENT per evitare il reload della pagina dovuto dal form -->
      <button class="ms-3 btn btn-warning" @click.prevent='resetSearch()'>RESET</button>
    </div>
  </form>
</template>

<script>
export default {
  name:'Search',
  data(){
    return{
      searchText:''
    }
  },
  methods:{
    resetSearch(){
      this.searchText=''
      this.startSearch();
    },
    startSearch(){
      this.$emit('ricercaPersonaggio',this.searchText) /* SCATENO L'EVENTO */
    }
  }
}
</script>

<style>
  input{
    margin-bottom: 40px;
  }
</style>