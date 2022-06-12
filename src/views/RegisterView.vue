<template >
  <div>
    <img alt="Bank logo" src="../assets/im1.png">
    <br><br>
    <h1>Register</h1>
    <br>
    <div class="Register" >
      <form action="">
        Nombre completo
        <input type="text" placeholder="Nombre completo" name="name" id="name">
        <br><br>
        Correo electronico
        <input type="text" placeholder="Correo electronico" name="email" id="email">
        <br><br>
        Contraseña
        <input type="text" placeholder="Contraseña" name="password" id="password">
        <br><br>
        Confirmar contraseña
        <input type="text" placeholder="Contraseña" name="confirmPassword" id="confirmPassword">
        <br><br>
        <a class="botonRegister" href="/" target="_blank">Registrarse</a>


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