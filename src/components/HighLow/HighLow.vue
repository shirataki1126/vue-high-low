<template>
  <div>
    <div v-show="!isPlaying">
      <v-row>
        <v-col>
          <v-btn block color="primary" v-on:click="start()">はじめる</v-btn>
        </v-col>
        <v-col v-if="!isFirstTime" cols="6">
          <v-btn block color="secondary" v-on:click="retry()">リトライ</v-btn>
        </v-col>
      </v-row>
    </div>
    <div v-show="isPlaying">
      <div>
        <Deck ref="parentDeck"></Deck>
      </div>
      <div>
        <Deck ref="playerDeck"></Deck>
      </div>
      <div v-if="!isEnded">
        <v-row>
          <v-col cols="6">
            <v-btn block color="primary" v-on:click="result(true)">ハイ</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn block color="secondary" v-on:click="result(false)">ロー</v-btn>
          </v-col>
        </v-row>
      </div>
      <div v-if="isEnded">
        <v-row>
          <v-col cols="12" class="text-center">
            {{this.resultMessage}}
          </v-col>
          <v-col cols="6">
            <v-btn block color="secondary" v-on:click="retry()">リトライ</v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn block color="gray" v-on:click="end()">おしまい</v-btn>
          </v-col>
        </v-row>
      </div>
    </div>
  </div>
</template>

<script>
import Deck from './Deck.vue'

export default {
  components: { Deck },
  data: () => ({
    isPlaying: false,
    isEnded: false,
    isFirstTime: true,
    resultMessage: ''
  }),
  methods: {
    start: function () {
      this.isEnded = false
      this.isPlaying = true
      if (this.isFirstTime) {
        this.isFirstTime = false
      }
      this.$refs.parentDeck.draw()
      this.$refs.parentDeck.draw()
      this.$refs.playerDeck.draw()
    },
    end: function () {
      this.$refs.parentDeck.initialize()
      this.$refs.playerDeck.initialize()
      this.isPlaying = false
    },
    retry: function () {
      this.$refs.parentDeck.initialize()
      this.$refs.playerDeck.initialize()
      this.isPlaying = true
      this.start()
    },
    result: function (isHigher) {
      this.$refs.parentDeck.draw()
      this.$refs.playerDeck.draw()
      this.$refs.playerDeck.draw()

      if ((this.$refs.parentDeck.getScore() < this.$refs.playerDeck.getScore()) === isHigher) {
        this.resultMessage = '当たり！'
      } else {
        this.resultMessage = 'はずれ！'
      }
      this.isEnded = true
    }
  }
}
</script>
