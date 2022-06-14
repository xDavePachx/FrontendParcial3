<template>
<div>
  <nav>
      <router-link to="/">Log out</router-link> |
      <router-link to="/ListUsersView">Lista de usuarios</router-link> |
      <router-link to="/ListTrans">Lista de transacciones</router-link>

    </nav>
    <router-view/>
  <h1>Realizar transaccion</h1>
  <div class="realizarTransaccion">
    <form action="">
        Nombre 
        <input v-model="name" placeholder="Nombre completo" type="text" name="name" id="name">
        <br><br>
        Fecha
        <input type="text" v-model="dateTrans" placeholder="Fecha de transaccion" name="dateTrans" id="dateTrans">
        Monto
        <input type="text" v-model="monto" placeholder="Monto" name="monto" id="monto">

        <br><br>
        <button type="button" v-on:click="realizarTrans" class="botonTrans">Realizar transaccion</button>
        
      </form>
  </div>
  

</div>
</template>
<script>
import axios from 'axios'

export default {
  name: "RealizarTransaccion",
  data() {
    return {
      name:"",
      dateTrans:"",
      monto:""
    }
  },
  methods: {
    async realizarTrans(){
      console.log(this.name)
      console.log(this.dateTrans)
      console.log(this.monto)

      const targetEndPoint = 'http://localhost:3000/realizar-transaccion'
      const payload = {name: this.name, dateTrans: this.dateTrans, monto: this.monto}

      
      try {
        const response = await axios.post(targetEndPoint, payload)
        console.log('respuesta del servidor', response)
        alert('Transaccion realizada')

        this.name = ""
        this.dateTrans = ""
        this.monto = ""
        
      } catch (error) {
        console.log('Error al realizar transaccion', error)
        alert('Error al realizar transaccion')

        
      }


    }
  }

}
</script>




<style scoped>
.botonTrans {
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