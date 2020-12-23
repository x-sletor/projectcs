<template>
  <v-bottom-navigation app fixed grow color="primary">
    <v-btn value="code" :to="{ name: 'News' }">
      <span>News</span>
      <v-icon color="purple darken-1">mdi-cat</v-icon>
    </v-btn>

    <v-btn value="favorites" :to="{ name: 'Qrkeep' }">
      <span>QR KEEP</span>
      <v-icon color="cyan lighten-2">mdi-paw</v-icon>
    </v-btn>
    <v-btn value="Scan" :to="{ name: 'Scan' }">
      <span>Scan</span>
      <v-icon color="light-green darken-1">mdi-call-split</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
export default {
  name: "BottomNav",
  data: () => ({
    drawer: null
  })
};
</script>
