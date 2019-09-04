<template>
  <v-col>
    <Card v-for="(cardRank, index) in this.hand" v-bind:key="index" v-bind:rank="cardRank"></Card>
  </v-col>
</template>

<script>
import Card from "./Card.vue";

export default {
  components: { Card },
  data: () => ({
    stock: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13],
    hand: []
  }),
  methods: {
    draw: function() {
      if (this.stock.length > 0) {
        const drawedCard = this.stock.splice(
          Math.floor(Math.random() * this.stock.length),
          1
        );
        this.hand.push(drawedCard[0]);
      } else {
        // 山札が0枚のとき
      }
    },
    
  }
};
</script>
