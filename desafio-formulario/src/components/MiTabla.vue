<template>
  <div class="table-container">
  <table>
    <thead>
      <tr>
        <th>Nombre</th>
        <th>Edad</th>
        <th>Email</th>
        <th>Password</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(usuario, index) in usuariosCopia" :key="index">
        <td>{{ usuario.nombre }}</td>
        <td>{{ usuario.edad }}</td>
        <td>{{ usuario.email }}</td>
        <td>{{ usuario.password }}</td>
      </tr>
    </tbody>
  </table>
  </div>
</template>
  
  <script>
  export default {
    name:'MiTabla',
    props: {
      usuarios: {
        type: Array,
        default: () => []
      }
    },
    computed: {
    usuariosCopia() {
      return [...this.usuarios]; // Obtener una copia de los usuarios
      }
    }
  };
  </script>

<style scoped>
.table-container {
  margin-top: 40px;
}

.table-container table {
  width: 100%;
  border-collapse: collapse;
}

.table-container th, .table-container td {
  padding: 10px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

.table-container th {
  background-color: #f2f2f2;
  font-weight: bold;
}

.table-container tr:hover {
  background-color: #f2f2f2;
  transition: background-color 0.3s ease;
}
</style>
