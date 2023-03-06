<script>
import axios from 'axios';
export default {
    data() {
        return {
            Nombre: "",
            Edad: "",
            EstadoCivil: "",
            Trabajo:"",
            Residencia: "",
            Cita: "",
            CitaAutor: "",
            Bio: "",
            Personalidad1: "50",
            Personalidad2:"50",
            Personalidad3: "50",
            Personalidad4: "50",
            Objetivos: [""] ,
            Frustraciones:[],
            Motivaciones: "",
        };
    },
    mounted() {
        

    },
    methods: {
        Enviar(){
            if(this.validar() ){
                axios.post("/api/guardarPersonasUxd.php", {
                nombre: this.Nombre,
                edad: this.Edad,
                estadoCivil: this.EstadoCivil,
                trabajo: this.Trabajo,
                residencia: this.Residencia,
                cita: this.Cita,
                citaAutor: this.CitaAutor,
                bio: this.Bio,
                personalidad01: this.Personalidad1,
                personalidad02: this.Personalidad2,
                personalidad03: this.Personalidad3,
                personalidad04: this.Personalidad4,
                objetivos: this.Objetivos,
                frustraciones: this.Frustraciones,
                motivaciones: this.Motivaciones,
                marcas: this.Marcas
                //completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
            })
            .then((response) => {
            console.log(response.status)
            });
            }

        },
        validar(){
//nombre
          if(this.Nombre != "" && !isNaN (this.Nombre) === false && this.Nombre.length <201 && this.Nombre.length > 2 ) {
            console.log("el nombre es correcto")
             
            //edad
            if (this.Edad.length < 3 && this.Edad != ""){
              console.log("edad existe")
            }else{
              console.log("no existe esa edad")
            }

            //Estado civil
            if (this.EstadoCivil != ""){
              console.log("si selecciono estado civil")
            }else{
              console.log("no selecciono estado civil")
              return false
            }

            //Trabajo
            if (this.Trabajo.length < 201 && this.Trabajo != "" && !isNaN (this.Trabajo) === false){
              console.log("trabajo existe")
            }else{
              console.log("no existe trabajo")
              return false
            }

            //Residencia
            if (this.Residencia.length < 201 && this.Residencia != "" && !isNaN (this.Residencia) === false){
              console.log("residencia existe")
            }else{
              console.log("no existe residencia")
              return false
            }

            //Cita
            if (this.Cita.length < 501 && this.Cita != "" && !isNaN (this.Cita) === false){
              console.log("Cita existe")
            }else{
              console.log("Cita no existe")
              return false
            }

            //CitaAutor
            if (this.CitaAutor.length < 501 && this.CitaAutor != "" && !isNaN (this.CitaAutor) === false){
              console.log("CitaAutor existe")
            }else{
              console.log("CitaAutor no existe")
              return false
            }

            //Bio
            if (this.Bio.length < 701 && this.Bio != "" && !isNaN (this.CitaAutor) === false){
              console.log("Bio correcta")
            }else{
              console.log("Bio incorrecta")
              return false
            }

          return true
                       
          }
          else{
            console.log("No pude registrarlo")
            return false
          }
          

            }



    }
}


</script>

<template>
    <div class="flex ">
        <div class="w-full rounded-lg p-6 shadow-lg bg-white m-4  ">
            <div class=" p-2 font-bold text-3xl" >
                <h1> Formulario de Registro</h1>
            </div>
            <div class="w-auto px-20  md:px-6">
                <form class=" mx-auto mb-4   " method="get">
                    <div class=" bg-orange-200 text-lg ">
                        <h1 class=" px-4   py-6 text-black text-3xl font-bold ">Información  Personal</h1>
                    <div class="lg:flex mb-2 px-4 py-3">
                        <div class="md:flex ">
                            
                    <label class="  block py-2 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Nombre: </label>
                    <input name="Nombre" id="Nombre" v-model="Nombre" class=" 2xl:w-96 sm:w-60 md:w-80  h-10 bg-while  appearance-none border-2 border-gray-200 rounded  py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500" type="text" >
                    
                </div>
                <div class="md:flex md:items-center mb-6">
                    
                    <label class=" px-6 block font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Edad:</label>
                    <input name="Edad" id="Edad" v-model="Edad" class="bg-while appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500"  type="text" >
                    
                </div>

                <div class=" md:flex md:items-center mb-5">

                <label class=" px-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Estado civil:
                </label>

                <div class="">
                <select v-model="EstadoCivil" name="EstadoCivil" id="EstadoCivil"  class="w-full py-2.5 px-4 rounded-lg bg-while focus:shadow focus:bg-white focus:outline-none">
                <option disabled  value="">Selecciona </option>
                <option value="1">Soltero</option>
                <option value="2">Casado </option>
                <option value="3">Divorciado</option>
                <option value="4">Separado</option>
                <option value="5">Unión libre</option>
                <option value="6">Viudo</option>
              </select>
                </div>
                    
                </div>

                </div>
                    
                <div class="lg:flex sm:py-2">
                    <div class="md:flex md:items-center mb-6">
                    <label class=" px-4 block text-black  font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Trabajo: </label>
                    <input name="Trabajo" id="Trabajo" v-model="Trabajo" class=" mb:w-80   2xl:w-96  bg-while appearance-none border-2 border-gray-200 rounded py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500" type="text" >
                </div>

                <div class="md:flex md:items-center mb-6">
                    <label class=" px-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Residencia </label>
                    <input name="Residencia" id="Residencia" v-model="Residencia" class=" mb:w-80   2xl:w-96 bg-while appearance-none border-2 border-gray-200 rounded  py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500"  type="text" >
                </div>

                </div>

            </div><br>

            <!-- Acerca de mi  -->

                <div class="bg-blue-200 py-2 px-5 w-full text-lg ">
                    <h1 class="text-3xl font-bold text-black  py-8">Acerca de mi</h1>
                <div class="lg:flex w-full">
                    <div class="md:flex md:items-center mb-6 lg:w-6/12 sm:w-full ">
                    <label class=" block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Cita:</label>
                     <textarea v-model="Cita"  name="cita" id="cita" class=" text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full" rows="1"></textarea>

                    </div>
                    <div class="md:flex md:items-center mb-6  lg:w-6/12 sm:w-full ">
                    
                    <label class="px-2  text-black font-bold w-32   sm:w-44 "> Cita autor: </label>
                    
                    <div class="w-11/12 ">
                     <textarea v-model="CitaAutor" name="citaAutor" id="citaAutor" class="text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full"  rows="2"></textarea>    
                    </div>
                </div>
                </div>



                <div class="md:flex md:items-center mb-6">
                    
                    <label class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Bio: </label>
                    
                    <div class="w-full">
                        <textarea name="Bio" id="Bio" class="text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full" v-model="Bio" rows="4"></textarea>
                    </div>
                    
                </div>
                </div>
                <br>
               
<div class="  bg-rose-200 px-4 py-8">
 <h1 class=" text-3xl font-bold">Personalidad</h1>
  <div class="w-full mt-4">
          <div class="px-8 text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 1.- Mente
          </label><br>
          <div class="flex">
          <h1 class="px-2">Extrovertido  {{ this.Personalidad1 }}% </h1>
          <input type="range" v-model="Personalidad1" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="Personalidad1" placeholder="" typeof="slider" min="0" max="100"/>
          <h1> Introvertido {{100- this.Personalidad1 }}% </h1>
          
        </div>

          </div>

  </div>
        


  <div class="w-full mt-4">
          <div class="px-8 text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 2.- Energía
          </label><br>

          <div class="flex">
          <h1 class="px-2">Intuitivo  {{ this.Personalidad2 }}% </h1>
          <input type="range" v-model="Personalidad2" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="Personalidad2" placeholder="" typeof="slider" min="0" max="100"/>
          <h1> Observador {{100- this.Personalidad2 }}% </h1>
          
        </div>

          </div>

  </div>

  <div class="w-full mt-4">
          <div class="px-8 text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 3.-Naturaleza
          </label><br>

          <div class="flex">
          <h1 class="px-2">Pensamiento  {{ this.Personalidad3 }}% </h1>
          <input type="range" v-model="Personalidad3" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="Personalidad3" placeholder="" typeof="slider" min="0" max="100"/>
          <h1> Emocional {{100- this.Personalidad3 }}% </h1>
          
        </div>


          </div>

  </div>

  <div class="w-full mt-4">
          <div class="px-8 text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 4.- Identidad
          </label><br>

          <div class="flex">
          <h1 class="px-2">Asertivo {{ this.Personalidad4 }}% </h1>
          <input type="range" v-model="Personalidad4" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="Personalidad4" placeholder="" typeof="slider" min="0" max="100"/>
          <h1> Cauteloso {{100- this.Personalidad4 }}% </h1>
          
        </div>

          </div>

  </div>
      




</div><br>

   <div class="bg-green-200 sm:px-4 lg:px-32 py-4" >
    <h1 class="text-3xl font-bold">Complementos</h1>
  
    
    <div class="flex mb-6 lg:w-4/5 sm:w-full px-2 py-2">
      <label class=" py-2 block text-black-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">  Objetivos: </label> 
      <input id="objetivos" name="objetivos" v-model="Objetivos" class="bg-white  appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-black leading-tight focus:outline-none focus:bg-white focus:border-black " type="text" >
    </div>

    <div class="flex mb-6 lg:w-4/5  sm:w-full px-2 py-2">
      <label class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Frustraciones:</label>
      <input id="frustaciones" name="frustraciones" v-model="Frustraciones" class="bg-whileappearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500"  type="text" >
                   
    </div>

    <div class="flex mb-6 lg:w-4/5  sm:w-full px-2 py-2">
      <label class="block text-black  font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Motivaciones:</label>       
      <input id="motivaciones"  name="motivaciones" v-model="Motivaciones" class="bg-while appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500"  type="text" >
              
    </div>

    <div class="flex mb-6 lg:w-4/5  sm:w-full  px-2 py-2">
      <label class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Marcas: </label>  
      <input v-model="Marcas" class="bg-while appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                     
    </div>

   </div>             

    <div class=" py-2">
                    
          <button  @click="Enviar()" class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="button">
            Enviar
          </button>
                    
    </div>
            </form>

            </div>
            
        </div>
    </div>
</template>