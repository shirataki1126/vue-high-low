<template>
  <v-content>
    <div>
      <v-row align="center" justify="center" class="flex-column flex-md-row flex-sm-row">
        <Deck ref="parentDeck"></Deck>
      </v-row>
      <v-btn block color="primary" v-on:click="parentDraw()">俺のターン！ドロー！</v-btn>
    </div>
    <div>
      <v-row align="center" justify="center" class="flex-column flex-md-row flex-sm-row">
        <Deck ref="playerDeck"></Deck>
      </v-row>
      <v-btn block color="primary" v-on:click="playerDraw()">俺のターン！ドロー！</v-btn>
    </div>
  </v-content>
</template>

<script>
import Deck from "./Deck.vue";

export default {
  components: { Deck },
  methods: {
    parentDraw: function() {
      this.$refs.parentDeck.draw();
    },
    playerDraw: function() {
      this.$refs.playerDeck.draw();
    }
  }
};
</script>
