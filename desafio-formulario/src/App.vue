<template>
  <div id="app">
    <MiFormularioVue @formulario-enviado="agregarUsuario" />
    <MiTabla :usuarios="usuariosCopia" />
  </div>
</template>

<script>
import MiTabla from './components/MiTabla.vue';
import MiFormularioVue from './components/MiFormulario.vue';

export default {
  name: 'App',
  components: {
    MiFormularioVue,
    MiTabla,
  },
  data() {
    return {
      usuarios: [],
      usuariosCopia:[]
    };
  },
  methods: {
    agregarUsuario(usuario) {
      this.usuarios.push(usuario);
      this.usuariosCopia = [...this.usuarios]; // Actualizar la copia de los usuarios
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
