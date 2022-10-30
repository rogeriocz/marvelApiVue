<template>
  <HeaderNav></HeaderNav>
  <main>
    <h1>
      <strong class="title"> Titulo de comic: {{ mangatitle }}</strong>
    </h1>

    <p>
      <strong class="title"> Titulo de comic: {{ mangadescrip }}</strong>
    </p>

    <PeliculaPrincipal />
    <TarjetasComic @emitiendoTitle="titleOfComic" />
  </main>
</template>

<script>
// @ is an alias to /src

import HeaderNav from "@/components/MarvelComics/HeaderNav.vue";
import PeliculaPrincipal from "@/components/MarvelComics/PeliculaPrincipal.vue";
import TarjetasComic from "@/components/MarvelComics/TarjetasComic.vue";

export default {
  name: "HomeView",
  data() {
    return {
      title: null,
      mangatitle: null,
      mangadescrip: null,
    };
  },
  components: {
    HeaderNav,
    PeliculaPrincipal,
    TarjetasComic,
  },

  methods: {
    titleOfComic(mangaTitle, mangaDescrip) {
      this.mangatitle = mangaTitle;
      this.mangadescrip = mangaDescrip;
      console.log("titleOfcomic", this.variableDeTarjeta);
    },
  },
};
</script>
<style>
:root {
  --rojo: #e50914;
  --fondo: #141414;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: var(--fondo);
  font-family: "Open Sans", sans-serif;
}

.title {
  background: var(--rojo);
}
</style>
