<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header class="">
    <div class="text-center rounded-full bg-blue-300 px-4 py-6">
    <h1 class="text-4xl font-bold  text-lime-700 "><strong>---Formulario de Personas UX</strong> </h1>
  </div><br>
  <div class=" bg-white px-4 py-4 ">
  
    <div class="wrapper">
      <HelloWorld msg="Formulario de personas UX" />

      
      <nav class="grid grid-cols-3 divide-x text-center">
      
        <RouterLink class="text-xl  bg-green-400 hover:bg-green-500 hover:text-2xl" to="/"> <strong>INICIO</strong> </RouterLink>
        <RouterLink class=" text-xl   bg-blue-400 hover:bg-blue-500 hover:text-2xl"  to="/personaUX"> <strong>Formulario </strong> </RouterLink>
        <RouterLink class=" text-xl   bg-red-400 hover:bg-red-500  hover:text-2xl"  to="/personas"> <strong> Ver persona</strong> </RouterLink>

      </nav>

      
    </div>


  <RouterView />
  </div>
  
  </header>

</template>

