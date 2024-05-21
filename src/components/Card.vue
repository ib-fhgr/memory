<template>

  <div class="flip-card-container">
      <!-- TODO: Wenn die Eigenschaft "flipped" der Karte "true" ist, dann soll der Titel der Karte angezeigt werden
           sonst nur eine leere Karte.

           Bonus: Implementieren Sie eine Animation, die die Karte um 180 Grad dreht, wenn sich die Eigenschaft "flipped" ändert
           Tipp: Fügen Sie eine Klasse hinzu, wenn die Karte "flipped" ist und entfernen Sie diese, wenn die Karte nicht "flipped" ist,
           dann können Sie die Animation per CSS definieren. -->
           
           <div :class="{hidden: !card.flipped, visible:card.flipped}">{{  card.title  }}</div>       
  </div>

</template>

<script>
export default {
  props: {
    // TODO: Definieren Sie die Eigenschaften der Karte
    card: Object,

  },
  data(){
    return {
      flipped: false,
    }
  
  }
};
</script>

<style>

.flip-card-container .hidden {
  opacity: 0;
  transition: opacity 1s;
}

.flip-card-container .visible {
  opacity: 1;
  transition: opacity 1s;
  background-color: khaki;
}

/* TODO: Definieren Sie die Styles für die Karte */
.flip-card-container {
  width: 100px;
  height: 100px;
  perspective: 1000px;
  border: black solid 1px;
  box-shadow: 5px 5px 5px lightgray;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  line-height: 100px;
}


</style>
