<template>
  <img class="animalImage" v-bind:src="card.image" alt="Animal Image" />
</template>

<script>
export default {
  props: ["card"],
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