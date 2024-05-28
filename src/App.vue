<script>
import CardList from './components/CardList.vue';
import HeaderApp from './components/HeaderApp.vue';
import store from './data/store.js';
import axios from 'axios';

export default {
  components: {
    CardList,
    HeaderApp,
  },
  data() {
    return {
      store,
      selectedArchetype: '',
    }
  },  

  methods: {
    mostraCarte(){
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then(risultato =>{
        this.store.carte = risultato.data.data;
      })
    }, 

    mostraArchetipi() {
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=" + this.selectedArchetype).then(risultato => {
      this.store.carte = risultato.data.data;
    })
    }
  },

  created() {

    this.mostraCarte(),

    this.mostraArchetipi(),

    axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then(risultato => {
      this.store.archetypes = risultato.data;
       
    })
    console.log(this.selectedArchetype)

  },

  mounted() {
    
  }
}
</script>

<template>
  <HeaderApp />
  <div class="position-absolute top-0 end-0">
    <label for="archetype-select">Seleziona Archetipo:</label>
    <select id="archetype-select" @change="mostraArchetipi" v-model="selectedArchetype">
      <option value="">Tutti</option>
      <option v-for="archetype in store.archetypes" :key="archetype" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>
    </select>
  </div>
  <CardList />
</template>

<style>
  label{
    color: white;
  }
</style>