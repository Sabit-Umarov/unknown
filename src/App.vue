<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-spacer></v-spacer>
      <v-btn color="accent" @click="random">Random</v-btn>
      <v-spacer></v-spacer>
      <h1 class="title">Click to reveal</h1>
      <v-spacer></v-spacer>
      <v-btn color="accent" @click="shuffleItems">Shuffle</v-btn>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <PageLayout ref="page" />
    </v-main>
  </v-app>
</template>

<script>
import PageLayout from "./components/PageLayout";

export default {
  name: "App",
  components: {
    PageLayout,
  },

  data: () => ({
    //
  }),
  methods: {
    shuffleItems() {
      this.$refs.page.shuffle();
    },
    random() {
      this.$refs.page.random();
    },
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 60px;
}
.v-main {
  background-color: #b71c1c !important;
}
</style>
