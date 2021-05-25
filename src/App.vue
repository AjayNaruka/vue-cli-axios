<template>
  <div id="app">
    <div v-if="!loading" class="container text-center mt-5">
      <h1>RICK & MORTY</h1>
      <Search
        @ricercaPersonaggio='searching'/>  <!-- RIMANE IN ATTESA DEL FLGIO CHE LANCIA L'EVENTO e parte la funzione searching che riceve i parametri dell emit -->
      <div class="row">
        <Card 
        v-for="card in filterCards"
        :key='card.id'
        :card='card'

        />
      </div>
    </div>
    <Loader v-else />
    
  </div>
</template>

<script>

import axios from 'axios'; /* cerco from axios( cerco in tutto il progetto) e la chiamo axios */
import Card from '@/components/Card'
import Loader from '@/components/Loader'
import Search from '@/components/Search'


export default {
  name: 'App',
  data(){
      return{
        axios,
        cards:[],
        loading:true,
        textToSearch: '',
      }
    },
  components: {
    Card,
    Loader,
    Search
  },
  methods:{
    searching(text){
      this.textToSearch=text;

    }
  },
  created(){
      axios.get('https://api.sampleapis.com/rickandmorty/characters')
        .then(res => {
          setTimeout(()=>{
            this.cards=res.data
            this.loading=false
          console.log(res.data)
          },2000)
          
        })
        .catch(err => {
          console.error(err); 
        })
      },
      computed:{
        filterCards(){
          let cleanArr= this.cards.filter(item => item.name!== undefined);
          if(this.textToSearch===''){
            return cleanArr
          }
            return cleanArr.filter(item => item.name.toLowerCase().includes(this.textToSearch.toLowerCase())) 
        }
      }
}
</script>

<style lang="scss">

  @import '@/assets/styles/general'
</style>
