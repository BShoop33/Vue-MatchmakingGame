<template>
  <div>
    <h1 class="header">Find all the matches</h1>
    <div class="cardsContainer">
      <div v-for="card in animalCards" :key="card.id">
        <animalCards :card="card" />
      </div>
    </div>
  </div>
</template>

<script>
import { animalImages } from "./components/cardData.js";
import animalCards from "./components/animalCard";

export default {
  components: { animalCards },

  data() {
    return { animalCards: [...animalImages] };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.cardsContainer {
  display: flex;
  flex-flow: row;
  flex-wrap: wrap;
  justify-content: center;
}

.header {
  text-align: center;
}
</style>
