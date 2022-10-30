<template>
  <marvel-api />
</template>

<script>
// @ is an alias to /src

import MarvelApi from "@/components/MarvelComics/MarvelApi.vue";

export default {
  name: "HomeView",

  components: {
    MarvelApi,
  },
};
</script>
