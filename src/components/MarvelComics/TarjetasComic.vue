<template>
  <div class="container">
    <div class="cards-comics" id="content">
      <div v-for="lista in comics" :key="lista.id" class="comic">
        <div class="face front">
          <img
            :src="`${lista.thumbnail.path}.${lista.thumbnail.extension}`"
            @click="EmitirManga"
          />
          <h4>{{ lista.title }}</h4>
        </div>
        <div
          class="face back"
          @click="$emit('emitiendoTitle', lista.title, lista.description)"
        >
          <h5>{{ lista.title }}</h5>
          <p>{{ lista.description }}</p>

          <div></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comics: [],
      manga: "Naruto",
    };
  },

  methods: {
    emitirManga() {
      this.$emit("EscucharManga", this.manga);
    },
    apiComicMarvel() {
      const apikey = "29d5c35f6659e38f56be597a5a502ddf";
      const ts = "01/10/2022, 00:11:08";
      const hash = "8d800c99e7e9b0f153ed642706300c28";
      const urlBase = "https://gateway.marvel.com:443/v1/public/";

      const url = `${urlBase}comics?apikey=${apikey}&ts=${ts}&hash=${hash}`;

      //console.log("Batman", url);
      fetch(url)
        .then((response) => response.json())
        .then((response) => {
          //this.comics = ;
          let revista = response.data.results;

          // esta
          this.comics = revista.filter(
            (revista) =>
              revista.thumbnail.path !=
              "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available"
          );
          console.log(this.comics);
          //return comics;
        });
    },

    /* emitirTitle() {
      this.$emit("emitiendoTitle", this.title);
      //console.log(this.title);
    }, */
  },
  async mounted() {
    try {
      await this.apiComicMarvel();
    } catch (error) {
      // error
    }
  },
};
</script>

<style>
.contenedor {
  width: 90%;
  margin: auto;
}

.comic {
  position: relative;
  width: 300px;
  height: 450px;
  margin: 20px;
}
.comic .face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  border-radius: 10px;
  overflow: hidden;
  transition: 0.5s;
}

.comic .front {
  transform: perspective(600px) rotateY(0deg);
  box-shadow: 0 5px 10px #000;
}

.comic .front img {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.comic .front h4 {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 45px;
  line-height: 45px;
  color: #fff;
  background: rgba(250, 2, 2, 0.993);
  text-align: center;
}

.comic .back {
  transform: perspective(600px) rotateY(180deg);
  background: rgb(3, 35, 54);
  padding: 15px;
  color: #f3f3f3;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  text-align: center;
  box-shadow: 0 5px 10px #000;
}

.comic .back .link {
  border-top: solid 1px #f3f3f3;
  height: 50px;
  line-height: 50px;
}

.comic .back .link a {
  color: #f3f3f3;
}

.comic .back h3 {
  font-size: 30px;
  margin-top: 20px;
  letter-spacing: 2px;
}
.comic .back p {
  letter-spacing: 1px;
}

.comic:hover .front {
  transform: perspective(600px) rotateY(180deg);
}
.comic:hover .back {
  transform: perspective(600px) rotateY(360deg);
}

.cards-comics {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

/* ---- ----- ----- Media Queries ----- ----- ----- */
@media screen and (max-width: 800px) {
  header .logotipo {
    margin-bottom: 10px;
    font-size: 30px;
  }

  header .contenedor {
    flex-direction: column;
    text-align: center;
  }

  .pelicula-principal {
    font-size: 14px;
  }

  .pelicula-principal .descripcion {
    max-width: 100%;
  }
}
</style>
