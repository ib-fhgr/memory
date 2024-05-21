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

    cardTitles = shuffleArray(cardTitles)

    for (let title of cardTitles) {
      this.cards.push({
        title: title,
        flipped: false, // wenn die Karte aufgedeckt ist, wird diese Eigenschaft auf true gesetzt
        matched: false  // wenn ein Kartenpaar gefunden wurde, wird diese Eigenschaft auf true gesetzt
      })
    }

    // Karten mischen
    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [array[i], array[j]] = [array[j], array[i]];
      }
      return array
    }

   

  },
  methods: {
    flippCard(card) {
      // Abbruch, wenn Karte bereits aufgedeckt, oder bereits 2 Karten aufgedeckt sind
      if (card.matched || card.flipped || this.flippedCards.length==2) return;

      if (this.flippedCards.length < 2 && card.matched == false) {
        // Karte aufdecken
        card.flipped = true
        this.flippedCards.push(card)
      }

      if (this.flippedCards.length === 2) {
        // Wenn nach dem Aufdecken 2 Karten aufgedeckt sind, prüfen ob diese identisch sind
        let [card1, card2] =this.flippedCards
        if (card1.title === card2.title) {
          card1.matched = true
          card2.matched = true
          let player = this.currentPlayer
          this.scores[player]++
          this.flippedCards = []
        } else {
          setTimeout(() => {
            card1.flipped = false
            card2.flipped = false
            this.flippedCards = []
            if (this.currentPlayer === "player1") {
              this.currentPlayer = "player2"
            } else {
              this.currentPlayer = "player1"
            }
          }, 2000);
        }
      }
    }
  }
};
</script>

<style scoped>
</style>
