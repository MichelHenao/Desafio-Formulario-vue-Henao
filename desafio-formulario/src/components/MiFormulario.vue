<template>
<form  class="formulario" @submit.prevent="submitForm">
  <h2>Formulario</h2>
    <div>
      <label for="nombre">Nombre:</label>
      <input type="text" id="nombre" v-model="formData.nombre" required>
    </div>
    <div>
      <label for="edad">Edad:</label>
      <input type="number" id="edad" v-model="formData.edad" required>
    </div>
    <div>
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="formData.email" required>
    </div>
    <div>
      <label for="password">Contraseña:</label>
      <input type="password" id="password" v-model="formData.password" required>
    </div>
    <!-- Agrega más inputs según sea necesario -->
    <button type="submit">Enviar</button>
  </form>
</template>

<script>
export default {
    name:'MiFormulario',
  data() {
    return {
      formData: {
        nombre: '',
        edad: '',
        email: '',
        password: ''
      }
    };
  },
  methods: {
    submitForm() {
      // Realiza las validaciones necesarias antes de enviar el formulario
      if (this.formData.nombre === '' || this.formData.edad === '' || this.formData.email === '' || this.formData.password === '') {
        alert('Por favor, completa todos los campos');
        return;
      }

       // Emitir los datos del formulario al componente padre
       this.$emit('formulario-enviado', {...this.formData});

// Reiniciar los campos del formulario
      this.resetFormData();
    },
    resetFormData() {
      this.formData.nombre = '';
      this.formData.edad = '';
      this.formData.email = '';
      this.formData.password = '';
    }
  }
};
</script>

<style scoped>
.formulario {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: rgba(255, 255, 255, 0.7);
  border: 1px solid #ddd;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.formulario label {
  display: block;
  margin-bottom: 5px;
  text-align: start;
}

.formulario input {
  width: 90%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.formulario button {
  display: block;
  width: 100%;
  padding: 10px;
  background-color: #3f51b5;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 10px;
}

.formulario button:hover {
  background-color: #303f9f;
}
</style>
