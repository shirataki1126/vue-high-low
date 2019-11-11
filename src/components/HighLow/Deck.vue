<template>
  <v-row>
    <v-col v-for="(card, index) in this.hand" v-bind:key="index" align="center" justify="center" cols="4">
      <Card v-bind:rank="card"></Card>
    </v-col>
  </v-row>
</template>

<script>
import Card from './Card.vue'

export default {
  components: { Card },
  data: () => ({
    stock: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13],
    hand: []
  }),
  methods: {
    draw: function () {
      if (this.stock.length > 0) {
        const drawedCard = this.stock.splice(
          Math.floor(Math.random() * this.stock.length),
          1
        )
        this.hand.push(drawedCard[0])
      } else {
        // 山札が0枚のとき
      }
    },
    getScore: function () {
      let score = this.hand.reduce((p, x) => (p += x), 0)
      return score
    },
    initialize: function () {
      this.stock = this.stock.concat(this.hand)
      this.hand = []
    }
  }
}
</script>
