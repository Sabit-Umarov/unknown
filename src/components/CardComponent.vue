<template>
  <v-card @click="reveal = !reveal">
    <v-card-text>
      <div class="title__container">
        <h1 class="title">{{ index }}</h1>
      </div>
    </v-card-text>

    <v-expand-transition>
      <v-card
        v-if="reveal"
        class="transition-fast-in-fast-out v-card--reveal"
        style="height: 100%"
      >
        <v-img height="360" :src="imageSrc"></v-img>
      </v-card>
    </v-expand-transition>
  </v-card>
</template>

<script>
export default {
  name: "CardComponent",
  data: () => ({
    reveal: false,
  }),
  props: {
    index: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    imageSrc() {
      return require(`../assets/${this.index}.jpg`);
    },
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 100px !important;
  &__container {
    height: 360px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.v-card--reveal {
  bottom: 0;
  opacity: 1 !important;
  position: absolute;
  width: 100%;
}
</style>
