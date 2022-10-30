<template>
  <div>
    <button @click="state = !state" role="button" class="boton">
      <i class="fas fa-info-circle"></i>{{ labelBtn }}
    </button>
  </div>
</template>
<script>
export default {
  name: "BotonHijo",
  data() {
    return {
      state: true,
      message: "Soy tu hijo",
    };
  },
  computed: {
    labelBtn() {
      this.$emit("stateUser", this.state);
      return this.state ? "activo" : "Inactivo";
    },
  },
};
</script>
