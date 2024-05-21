<template>
  <div class="game-board">
    
    <!-- TODO: Für jede Karte in der Eigenschaft "cards" soll ein Card-Component gerendert werden 
         und die Eigenschaften der Karte an das Card-Component übergeben werden. 

        Wenn die Karte angeklickt wird, soll die Methode "flippCard" aufgerufen werden und die Karte als Argument übergeben werden.

        Das Layout soll so sein, dass die Karten in einer 5x5 Grid angeordnet sind - Tipp, dies kann man per CSS umsetzen.      
    -->
  
  </div>
</template>

<script>
import Card from './Card.vue'

export default {  
  components: {
    /* TODO: Kartenkomponente hinzufügen */
  },
  props: {
    /* TODO: Definieren Sie eine Eigenschaft "cards" */
  },
  methods: {
    flippCard(card) {
      // sendet ein Event "flippCard" mit der Karte als Argument an die Elternkomponente
      this.$emit('flippCard', card);
    }
  },
  
};
</script>

<style>

/* TODO: Definieren Sie die Styles für das Spielfeld, Tipp: CSS-Grid */

</style>
