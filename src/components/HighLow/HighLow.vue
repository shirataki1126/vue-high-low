<template>
  <v-content>
    <div v-show="!isPlaying">
      <v-btn color="primary" v-on:click="start()">はじめる</v-btn>
      <v-btn v-if="!isFirstTime" color="secondary" v-on:click="retry()">リトライ</v-btn>
    </div>
    <div v-show="isPlaying">
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
      <v-btn color="secondary" v-on:click="end()">ええい、もう終いじゃ！</v-btn>
    </div>
  </v-content>
</template>

<script>
import Deck from "./Deck.vue";

export default {
  components: { Deck },
  data: () => ({
    isPlaying: false,
    isFirstTime: true
  }),
  methods: {
    start: function() {
      this.isPlaying = true;
      if (this.isFirstTime) {
        this.isFirstTime = false;
      }
    },
    end: function () {
      this.isPlaying = false;
    },
    retry: function () {
      this.isPlaying = true;
    },
    parentDraw: function() {
      this.$refs.parentDeck.draw();
    },
    playerDraw: function() {
      this.$refs.playerDeck.draw();
    }
  }
};
</script>
