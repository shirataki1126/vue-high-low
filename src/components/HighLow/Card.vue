<template>
  <v-card max-width="200px">
    <v-card-text>{{ this.rank }}</v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    rank: Number
  }
}
</script>
