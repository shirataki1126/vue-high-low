<template>
  <v-app>
    <v-content>
      <AppBar></AppBar>
      <v-container>
        <HighLow></HighLow>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import AppBar from './components/Bars/AppBar'
import HighLow from './components/HighLow/HighLow'

export default {
  components: {
    AppBar,
    HighLow
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Kosugi+Maru&display=swap");

html {
  font-family: "Kosugi Maru", sans-serif;
}
</style>
