<script>

import AppHeader from "./components/AppHeader.vue";
import AppCards from "./components/AppCards.vue";
import AppLoader from "./components/AppLoader.vue";
import AppSearch from "./components/AppSearch.vue";
import { store } from "./store.js";

export default {
  data() {
    return {

      store,
    };
  },

  components: {
    AppHeader,
    AppCards,
    AppSearch,
    AppLoader,
  },
};
</script>

<template>
  <AppHeader></AppHeader>
  <!-- <AppLoader v-if="!store.cards.length > 0"></AppLoader> -->
  <AppCards> </AppCards>
</template>

<style lang="scss" scoped></style>