<template>
  <div class="pelicula-principal">
    <div class="contenedor">
      <h3 class="titulo">{{ state }} {{ variableRecibida }}</h3>
      <p class="descripcion">
        Riri Williams, no es la primera mujer en llevar una armadura de Iron
        Man, pero si es la primera mujer afroamericana en usar la tecnología del
        Hombre de Hierro, y, sobre todo, es la primera que ha diseñado su propia
        armadura utilizando ingeniería inversa. Ironheart debutó en el
        Invincible Iron Man # 7 de Brian Michael Bendis y Mike Deodato.
      </p>

      <botonHijo @stateUser="state = $event" />
      <botonHijoDos @escucharHijo="variableHijo" />

      <h4>{{ myMessage }}</h4>
    </div>
  </div>
</template>

<script>
import botonHijo from "./BotonHijo.vue";
import botonHijoDos from "./BotonHijoDos.vue";

export default {
  name: "PeliculaPrincipal",
  data() {
    return {
      state: true,
      myMessage: "",
      variableRecibida: null,
    };
  },

  components: { botonHijo, botonHijoDos },

  methods: {
    handleMessage(value) {
      this.myMessage = value;
    },

    variableHijo(dataValue) {
      this.variableRecibida = dataValue;
    },
  },
};
</script>
<style>
/* ---- ----- ----- Pelicula Principal ----- ----- ----- */
.pelicula-principal {
  font-size: 16px;
  min-height: 40.62em;
  color: #fff;
  background: linear-gradient(rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.5) 100%),
    url(@/assets/img/ironheart.jpg);
  background-position: center center;
  background-size: cover;
  margin-bottom: 3.12em;
  display: flex;
  align-items: end;
}

.pelicula-principal .contenedor {
  margin: 0 auto;
  margin-bottom: 6.25em;
}

.pelicula-principal .titulo {
  font-weight: 600;
  font-size: 3.12em;
  margin-bottom: 0.4em;
}

.pelicula-principal .descripcion {
  font-weight: normal;
  font-size: 1em;
  line-height: 1.75em;
  max-width: 50%;
  margin-bottom: 1.25em;
}

.pelicula-principal .boton {
  background: rgba(0, 0, 0, 0.5);
  border: none;
  border-radius: 0.31em;
  padding: 0.93em 1.87em;
  color: #fff;
  margin-right: 1.25em;
  cursor: pointer;
  transition: 0.3s ease all;
  font-size: 1.12em;
}

.pelicula-principal .boton:hover {
  background: #fff;
  color: #000;
}

.pelicula-principal .boton i {
  margin-right: 1.25em;
}
</style>
