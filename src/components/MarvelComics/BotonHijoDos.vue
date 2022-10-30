<template>
  <div>
    <button role="button" @click="EnviarAlPadre()" class="boton">
      <i class="fas fa-info-circle"></i>Enviar al padre
    </button>
  </div>
</template>
<script>
export default {
  name: "BotonHijoDos",
  data() {
    return { NumeroInsertadoHijo: 5 };
  },
  methods: {
    EnviarAlPadre() {
      this.$emit("escucharHijo", this.NumeroInsertadoHijo);
    },
  },
};
</script>
