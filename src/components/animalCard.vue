<template>
  <img
    class="animalImage"
    @click="handleClick"
    v-bind:src="cardView"
    alt="Animal Image"
  />
</template>

<script>
export default {
  props: ["card"],

  data() {
    return {};
  },

  methods: {
    handleClick() {
      this.$emit("toggle", this.card);
    },
  },

  computed: {
    cardView() {
      return this.card.answerShown
        ? this.card.image
        : "https://www.onoursleeves.org/-/media/nch/giving/images/on-our-sleeves-1010/icons/icon-teasers/w45084_iconcollectionlandingiconteaserimages_questionmark.jpg";
    },
  },
};
</script>

<style>
.animalImage {
  border: 3px;
  border-color: black;
  border-style: solid;
  height: 16em;
  margin: 0.25em;
  width: 16em;
}
</style>