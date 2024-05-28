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
    }
  },
  methods: {
    
  },

  created() {

    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then(risultato => {
      this.store.carte = risultato.data.data;
    })
    console.log(store)

  },

  mounted() {
    
  }
}
</script>

<template>
  <HeaderApp />
  <CardList />
</template>

<style>

</style>