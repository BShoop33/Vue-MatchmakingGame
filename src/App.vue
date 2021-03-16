<template>
  <div>
    <div class="cardsContainer">
      <div v-for="card in animalCards" :key="card.id">
        <animalCards
          :card="card"
          @toggle="handleToggle"
          :guess1="guess1"
          :guess2="guess2"
        />
      </div>
    </div>
  </div>
</template>

<script>
import animalCards from "./components/animalCard";
import getAnimalImages from "./components/cardData.js";
import shuffle from "lodash.shuffle";

export default {
  components: { animalCards },

  data() {
    return {
      animalCards: shuffle(getAnimalImages()),
      guess1: null,
      guess2: null,
    };
  },

  methods: {
    handleToggle(cardClicked) {
      if (this.guess1 === null) {
        this.guess1 = cardClicked;
        return;
      }

      if (this.guess1 === cardClicked) return;

      this.guess2 = cardClicked;

      const [animal1, animal2] = this.getAnimalImages(cardClicked.name);

      if (this.guess1.name === this.guess2.name) {
        animal1.foundMatch = true;
        animal2.foundMatch = true;
        this.guess1 = null;
        this.guess2 = null;
      } else {
        setTimeout(() => {
          this.guess1 = null;
          this.guess2 = null;
        }, 1000);
      }
    },

    getAnimalImages(name) {
      return this.animalCards.filter((l) => l.name === name);
    },
  },

  computed: {
    foundAllMatches() {
      return this.card.every((l) => l.foundMatch);
    },
  },
};
</script>

<style>
.cardsContainer {
  display: flex;
  flex-flow: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>