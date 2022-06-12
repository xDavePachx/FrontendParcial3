<template>
<div>
  <h1>Realizar transaccion</h1>
  <div class="realizarTransaccion">
    <form action="">
        
        <input type="hidden" name="idTransaccion" id="idTransaccion">
        <br><br>
        Fecha
        <input type="text" placeholder="Fecha de transaccion" name="dateTrans" id="dateTrans">
        Monto
        <input type="text" placeholder="Monto" name="monto" id="monto">

        <br><br>
        <a class="botonTrans" href="" target="_blank">Realizar transaccion</a>
        
      </form>
  </div>
  

</div>
  
</template>
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