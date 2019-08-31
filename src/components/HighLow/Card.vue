<template>
  <v-card>
    <v-card-text>{{ this.rank }}</v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    rank: Number
  }
};
</script>
