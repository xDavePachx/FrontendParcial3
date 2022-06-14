<script>
import axios from 'axios'


export default {
  name: "RegisterUser",
  data() {
    return {
      name:"",
      email:"",
      password:"",

    }
  },
  methods: {
    async createUser(){
      console.log(this.name)
      console.log(this.email)
      console.log(this.password)

      //esta es una prueba que hice
      const test = await axios.get('http://localhost:3000/test')
      console.log('lo que trae test', test)

      //esta accede a mi endpoint register
      const targetEndPoint = 'http://localhost:3000/register'
      const payload = {name: this.name, email: this.email, password: this.password}

      try {
        const response = await axios.post(targetEndPoint, payload)
        console.log('respuesta del servidor', response)
        alert('Usuario registrado')

        this.name = ""
        this.email = ""
        this.password = ""
        
      } catch (error) {
        console.log('Error registrando usuario', error)
        alert('Error al registrar usuario')

        
      }

    }
  },
  
    
  }
</script>

<template >
  <div>
    <nav>
      <router-link to="/">Login</router-link> |
      <router-link to="/RegisterView">Register</router-link>
    </nav>
    <router-view/>
    <img alt="Bank logo" src="../assets/im1.png">
    <br><br>
    <h1>Register</h1>
    <br>
    <div class="Register" >
      <form action="">
        Nombre completo
        <input type="text" v-model="name" placeholder="Nombre completo" name="name" id="name">
        <br><br>
        Correo electronico
        <input type="text" v-model="email" placeholder="Correo electronico" name="email" id="email">
        <br><br>
        Contraseña
        <input type="password" v-model="password" placeholder="Contraseña" name="password" id="password">
        <br><br>
        <br><br>
        <button type="button" v-on:click="createUser" class="botonRegister">Register</button>


      </form>
    </div>
  </div>

</template>


<style scoped>
.botonRegister {
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