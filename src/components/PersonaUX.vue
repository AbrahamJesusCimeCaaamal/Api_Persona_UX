<script>
import axios from 'axios'


export default {

  methods: {
 RegistroUX(){
  axios
.post("/api/guardarPersonasUxd.php", {
nombre: this.nombre,
objetivos:this.objetivos,
frustraciones: this.frustraciones,
motivaciones: this.motivaciones,
marcas: this.marcas,
//completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
})
.then((response) => {
console.log(response.status)
});
  

 }
   
  },

  }

  



</script>

<template>






 
</template>