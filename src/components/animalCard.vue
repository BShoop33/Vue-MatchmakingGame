<template>
  <div class="card" :class="{ flipped: isShown }">
    <div class="card-inner" @click="handleClick">
      <div class="back-side">
        <img
          class="animalImage"
          src="https://www.onoursleeves.org/-/media/nch/giving/images/on-our-sleeves-1010/icons/icon-teasers/w45084_iconcollectionlandingiconteaserimages_questionmark.jpg"
          alt="hidden card"
        />
      </div>
      <div class="animal-side">
        <img
          class="animalImage"
          v-bind:src="card.image"
          :alt="card.name"
          :title="card.name"
        />
        <h3 class="cardName">{{ card.name }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["card", "guess1", "guess2"],

  methods: {
    handleClick() {
      this.$emit("toggle", this.card);
    },
  },

  computed: {
    isShown() {
      return (
        this.card.foundMatch ||
        this.card === this.guess1 ||
        this.card === this.guess2
      );
    },
  },
};
</script>

<style scoped>
.animalImage {
  background-color: transparent;
  height: 14em;
  perspective: 1000px;
  width: 16em;
}

.animal-side {
  background-color: lightskyblue;
  color: black;
  transform: rotateY(180deg);
}

.back-side {
  background-color: lightskyblue;
}

.back-side,
.animal-side {
  position: absolute;
  width: 100%;
  height: 100%;
}

.card {
  border: 3px;
  border-color: black;
  border-style: solid;
  height: 16em;
  margin: 0.25em;
  width: 16em;
  background-color: transparent;
  perspective: 1000px;
  margin-top: 20px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.5s;
  transform-style: preserve-3d;
}

.cardName {
  margin-top: -0.05em;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}
</style>