<template>
<div>
  <nav>
    <router-link to="/">Log out</router-link> |
    <router-link to="/RealizarTransaccion">Realizar transaccion</router-link> |
    <router-link to="/ListUsersView">Lista de usuarios</router-link>
  </nav>
  <router-view/>

  <h1>Lista de transacciones</h1>
  <div class="table-container">
    
  <table class="table1">
    <thead>
      <tr>
        <td>ID</td>
        <td>Nombre</td>
        <td>Fecha</td>
        <td>Monto</td>
        <td>Fecha de creacion</td>
        <td>Fecha de actualizacion</td>
        <td>Accion</td>
      </tr>
    </thead>
    <tbody>
      <tr v-for="transaccion in listadoTransacciones" :key="transaccion.id">
        <td>{{transaccion.id}}</td>
        <td>{{transaccion.name}}</td>
        <td>{{transaccion.dateTrans}}</td>
        <td>{{transaccion.monto}}</td>
        <td>{{transaccion.createdAt}}</td>
        <td>{{transaccion.updatedAt}}</td>
        <td><button v-on:click="eliminarTrans(transaccion.id)">Eliminar</button></td>
      </tr>
    </tbody>
  </table>

  </div>

  <button type="button" v-on:click="listaTransacciones" class="botonList">Mostrar</button>


</div>  
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      listadoTransacciones: []
    }
    
  },
  methods: {
    async listaTransacciones(){
      
      const listTrans = await axios.get('http://localhost:3000/listar-transacciones')
      console.log('Extraido de la base de datos', listTrans.data.data)
      this.listadoTransacciones = listTrans.data.data
    },

    async eliminarTrans(inputId) {
      console.log('id de db', inputId)
      console.log('inputid',typeof(inputId))


      const targetEndPoint = `http://localhost:3000/delete-transaccion/${inputId}`

      try {
        const response = await axios.delete(targetEndPoint)
        alert('Transaccion eliminada', response)
        this.listaTransacciones()
        
      } catch (error) {
        alert('Error al tratar de eliminar una transaccion',error)
        
        
      }
    }
  }
}
</script>
<style>
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
.table1 {
  margin: auto;
  background: #d5b0b4;

}
.table-container{


}

</style>