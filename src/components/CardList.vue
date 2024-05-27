<script>
import  store  from '../data/store.js'
import SingleCard from './SingleCard.vue';

 export default {
  name:"CardList",
  components: {
    SingleCard
  },
  data() {
    return {
      store
    }
  }
}
</script>

<template>
  <div class="card-list">
    <SingleCard v-for="card in store.carte" :key="card.name"  :carta="card" />
  </div>
</template>

<style scoped>
  .card-list {
  display: flex;
  flex-wrap: wrap;
  width: 70%;
  margin: 0 auto;
  padding: 1rem 3rem;
}

</style>