<script>
  export default {
  name: "SingleCard",
  props: {
    carta: Object
  }
};
</script>

<template>
  <div class="card">
    <img :src="carta.card_images[0].image_url" :alt="carta.name" class="card-image" />
    <h2 class="card-name">{{ carta.name }}</h2>
    <p class="card-archetype">{{ carta.archetype }}</p>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ccc;
  padding: 0.5rem;
  width: calc(100% / 5);
  text-align: center;
  background-color: orange;
}

.card-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.card-name {
  font-size: 18px;
  margin: 10px 0;
}

.card-archetype {
  font-size: 14px;
  color: #666;
}
</style>