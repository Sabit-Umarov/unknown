<template>
  <v-container class="mt-10" :key="parentKey">
    <v-row class="text-center">
      <v-col cols="12" md="6" lg="3" v-for="index in images" :key="index">
        <CardComponent :index="index" />
      </v-col>
    </v-row>
    <v-overlay z-index="999" :value="overlay" opacity="1">
      <v-card width="360" class="pb-4" light>
        <v-card-text class="pb-0">
          <v-img height="360" :src="overlayImage" class="mb-4"></v-img>
        </v-card-text>
        <div class="overlay__actions-container">
          <v-btn
            class="white--text overlay__close-button"
            color="#3F51B5"
            @click="randomizeOverlayImage"
            width="100%"
          >
            Another one
          </v-btn>
          <v-btn
            class="white--text"
            color="primary"
            @click="overlay = false"
            width="100%"
          >
            Close
          </v-btn>
        </div>
      </v-card>
    </v-overlay>
  </v-container>
</template>

<script>
import CardComponent from "./CardComponent.vue";

export default {
  name: "PageLayout",
  components: {
    CardComponent,
  },
  data: () => ({
    images: [],
    parentKey: 1,
    overlay: false,
    overlayImage: "",
  }),
  created() {
    this.renderImages();
  },
  methods: {
    renderImages() {
      for (let i = 1; i < 85; i++) {
        this.images.push(i);
      }
    },
    shuffle() {
      this.images = this.shuffleArray(this.images);
      this.parentKey++;
    },
    shuffleArray(array) {
      let currentIndex = array.length,
        randomIndex;

      // While there remain elements to shuffle.
      while (currentIndex != 0) {
        // Pick a remaining element.
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex--;

        // And swap it with the current element.
        [array[currentIndex], array[randomIndex]] = [
          array[randomIndex],
          array[currentIndex],
        ];
      }

      return array;
    },
    random() {
      const randomIndex = Math.floor(Math.random() * 84) + 1;
      this.overlayImage = require(`../assets/${randomIndex}.jpg`);
      this.overlay = true;
    },
    randomizeOverlayImage() {
      this.random();
    },
  },
};
</script>

<style lang="scss" scoped>
.overlay {
  &__actions-container {
    padding: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__close-button {
    margin-bottom: 16px;
  }
}
</style>
