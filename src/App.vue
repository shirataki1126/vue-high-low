<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>ハイ＆ロー</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <span class="mr-2">ぬるぽ</span>
    </v-app-bar>

    <v-content>
      <HighLow />
    </v-content>
    <v-content></v-content>
  </v-app>
</template>

<script>
import HighLow from "./components/HighLow/HighLow.vue";

export default {
  components: { HighLow }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Kosugi+Maru&display=swap');

#app {
  font-family: 'Kosugi Maru', sans-serif;
}
</style>
