<template>
  <div class="hello">
    <nav>
      <router-link to="/">Login</router-link> |
      <router-link to="/RegisterView">Register</router-link>
    </nav>
    <router-view/>
    <img alt="Bank logo" src="../assets/im1.png">
    <br><br><br>

    <h1>Login</h1>
    <br>
    <div class="login" >
      <form action="">
        Correo electronico
        <input type="text" v-model="email" placeholder="Correo electronico" name="email" id="email">
        <br><br>
        Contraseña
        <input type="password" v-model="password" placeholder="Contraseña" name="password" id="password">
        <br><br>
        <button type="button" v-on:click="IniciarSesion" class="botonLogin">Login</button>

      </form>
      

    </div>


  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data(){
    return{
      email: "", 
    password: "",
    }

  },
  props: {
    msg: String,

  },
  methods: {
    async IniciarSesion(){
      console.log(this.email)
      console.log(this.password)

      const targetEndPoint = 'http://localhost:3000/login'
      const payload = {email: this.email, password: this.password }

      try {
        const response = await axios.post(targetEndPoint, payload)
        console.log('respuesta servidor', response)
        alert('Ingreso con exito')

        return this.$router.push('/ListUsersView')
        
      } catch (error) {
        console.log('Error al iniciar sesion', error)
        alert('Error al iniciar sesion')
        
      }
    }
  }
  
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.botonLogin {
  border: 1px solid #2e518b; /*anchura, estilo y color borde*/
  padding: 10px; /*espacio alrededor texto*/
  background-color: #cf2610; /*color botón*/
  color: #ffffff; /*color texto*/
  text-decoration: none; /*decoración texto*/
  text-transform: uppercase; /*capitalización texto*/
  font-family: 'Helvetica', sans-serif; /*tipografía texto*/
  border-radius: 50px; /*bordes redondos*/
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
