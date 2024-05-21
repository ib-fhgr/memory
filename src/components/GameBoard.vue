<template>
  <div class="game-board">
    <!-- Rendering each card as a Card component and passing properties -->
    <Card
      v-for="card in cards"
      :card="card"
      @click="flippCard(card)"
    />
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
  components: {
    Card
  },
  props: {
    cards: {
      type: Array,
      required: true
    }
  },
  methods: {
    flippCard(card) {
      this.$emit('flippCard', card);
    }
  }
};
</script>

<style>
.game-board {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 10px; /* Adjust as needed for spacing between cards */
}
</style>