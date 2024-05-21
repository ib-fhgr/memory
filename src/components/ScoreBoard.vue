<template>
  <div class="score-board">
    <p id="player1">Spieler 1: {{ scores.player1 }}</p>
    <p id="player2">Spieler 2: {{ scores.player2 }}</p>
    <p id="player1" v-if="currentPlayer == 'player1'"><strong>Spieler 1 ist am Zug</strong></p>
    <p id="player2" v-if="currentPlayer == 'player2'"><strong>Spieler 2 ist am Zug</strong></p>
  </div>
</template>

<script>
export default {
  props: {
    scores: {
      type: Object,
      required: true
    },
    currentPlayer: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.score-board {
  text-align: center;
  font-size: 1.2em;
  margin: 10px;
  font-family: Helvetica;
  border-width: 2pt;
  border-style: solid;
  border-color: black;
}

#player1 {
  color: red
}

#player2 {
  color: rgb(24, 47, 194)
}


</style>