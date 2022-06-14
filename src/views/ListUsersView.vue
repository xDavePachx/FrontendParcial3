<template>
<div>
  <nav>
      <router-link to="/">Log out</router-link> |
      <router-link to="/RealizarTransaccion">Realizar transaccion</router-link> |
      <router-link to="/ListTrans">Lista de transacciones</router-link>

    </nav>
    <router-view/>

  <h1>Lista de usuarios</h1>
  <div class="table2-container">
    
  <table class="table2">
    <thead>
      <tr>
        <td>ID</td>
        <td>Nombre</td>
        <td>Correo</td>
        <td>Fecha de creacion</td>
        <td>Fecha de actualizacion</td>
        <td>Accion</td>
      </tr>
    </thead>
    <tbody>
      <tr v-for="listUser in listadoUsuarios" :key="listUser.id">
        <td>{{listUser.id}}</td>
        <td>{{listUser.name}}</td>
        <td>{{listUser.email}}</td>
        <td>{{listUser.createdAt}}</td>
        <td>{{listUser.updatedAt}}</td>
        <td><button v-on:click="eliminarUsuario(listUser.id)">Eliminar</button></td>
      </tr>
    </tbody>
  </table>

  </div>

  <button type="button" v-on:click="solicitarUsuarios" class="botonList">Mostrar</button>



  

</div>

</template>
<script>
import axios from 'axios'

export default {
  name: "solicitarUsuariosRegistrados",
  data(){
    return {
      listadoUsuarios: []
      

    }

  },
  methods:{
    async solicitarUsuarios(){

    try {
      const listaUsuarios = await axios.get('http://localhost:3000/list-users')
      console.log('lo que se trae de base de datos', listaUsuarios.data.data)
      this.listadoUsuarios = listaUsuarios.data.data
      
    } catch (error) {
      alert('fallo al extraer listado de usuarios')
      
    }

    },

    async eliminarUsuario(inputId) {
      console.log('id db', inputId)

      const targetEndPoint = `http://localhost:3000/delete-user/${inputId}`

      try {
        const response = await axios.delete(targetEndPoint)
        alert('Usuario eliminado',response)
        this.solicitarUsuarios()

      } catch (error) {
        alert('Error al tratar de eliminar usuario',error)
        
      }
      

    }

  }
}
</script>

<style scoped>
.table2 {
  margin: auto;
  background: #d5b0b4;

}
.botonList {
  border: 1px solid #2e518b; /*anchura, estilo y color borde*/
  padding: 10px; /*espacio alrededor texto*/
  background-color: #cf2610; /*color botón*/
  color: #ffffff; /*color texto*/
  text-decoration: none; /*decoración texto*/
  text-transform: uppercase; /*capitalización texto*/
  font-family: 'Helvetica', sans-serif; /*tipografía texto*/
  border-radius: 50px; /*bordes redondos*/
}

</style>