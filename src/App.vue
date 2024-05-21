<template>
  <header>
    <h1>Memory</h1>
    <ScoreBoard :currentPlayer="currentPlayer" :scores="scores"/>
  </header>

  <main>
    <GameBoard :cards="cards" @flippCard="flippCard">
    </GameBoard>
  </main>
</template>


<script>
import ScoreBoard from './components/ScoreBoard.vue'
import GameBoard from './components/GameBoard.vue'

export default {
  components: {
    ScoreBoard,
    GameBoard
  },
  data() {
    return {
      cards: [],
      flippedCards: [],
      scores: {
        player1: 0,
        player2: 0
      },
      currentPlayer: 'player1'
    };
  },
  mounted() {
    // erzeugt 20 Kartenobjekte
    let cardTitles = ['A', 'A', 'B', 'B', 'C', 'C', 'D', 'D', 'E', 'E', 'F', 'F', 'G', 'G', 'H', 'H', 'I', 'I', 'J', 'J'];

    for (let title of cardTitles) {
      this.cards.push({
        title: title,
        flipped: false, // wenn die Karte aufgedeckt ist, wird diese Eigenschaft auf true gesetzt
        matched: false  // wenn ein Kartenpaar gefunden wurde, wird diese Eigenschaft auf true gesetzt
      })
    }

    // TODO: Karten mischen
  },
  methods: {
    flippCard(card) {
      // Abbruch, wenn Karte bereits aufgedeckt, oder bereits 2 Karten aufgedeckt sind
      if (card.matched || card.flipped || this.flippedCards.length==2) return;

      if (this.flippedCards.length < 2 && card.matched == false) {
        // TODO: Karte aufdecken
      }

      if (this.flippedCards.length === 2) {
        // TODO: Wenn nach dem Aufdecken 2 Karten aufgedeckt sind, prüfen ob diese identisch sind

        // Falls ja, Punkte vergeben und Karten aufgedeckt lassen

        // Falls nein:
        // - 2 Sekunden warten
        // - Karten wieder umdrehen
        // - Spieler wechseln
      }
    }
  }
};
</script>

<style scoped>
</style>
