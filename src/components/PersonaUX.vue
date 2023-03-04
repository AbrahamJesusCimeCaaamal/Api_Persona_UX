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
            Personalidad1: "",
            Personalidad2:"",
            Personalidad3: "",
            Personalidad4: "",
            Objetivos: [""] ,
            Frustraciones:[],
            Motivaciones: "",
        };
    },
    mounted() {
        

    },
    methods: {
        Enviar(){
            if(this.validarNombre() ){
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

        validarNombre(){
            if (this.Nombre == "") {
                console.log("vamos, ponle un nombre")
                return false
            }else{
                console.log("vamos") 
            }
            return true
            

        }

    }
}


</script>

<template>
    <div class="flex ">
        <div class="w-full rounded-lg p-6 shadow-lg bg-white ">
            <div class=" p-2 font-bold text-3xl" >
                <h1> Formulario de Registro</h1>
            </div>
            <div class="w-auto px-20  md:px-6">
                <form class=" mx-auto mb-4   " method="get">
                    <div class=" bg-orange-200 text-lg ">
                        <h1 class="text-left px-4   py-6 text-black text-2xl font-bold ">Parte 1.- Información  Personal</h1>
                    <div class="md:flex mb-2 px-4 py-3">
                        <div class="flex ">
                            
                    <label class="  block py-2 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Nombre: </label>
                    <input name="Nombre" id="Nombre" v-model="Nombre" class="w-96 h-10 bg-gray-100 appearance-none border-2 border-gray-200 rounded  py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500" type="text" >
                    
                </div>
                <div class="md:flex md:items-center mb-6">
                    
                    <label class=" px-6 block font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Edad:</label>
                    <input name="Edad" id="Edad" v-model="Edad" class="bg-gray-100 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500"  type="text" >
                    
                </div>

                <div class="flex md:items-center mb-5">

                <label class=" px-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Estado civil:
                </label>

                <div class="">
                 <select name="EstadoCivil" id="EstadoCivil" class=" px-6 py-2 bg-gray-50  border-gray-100 text-gray-900 text-lg rounded-lg border-2 focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="EstadoCivil"  >
                <option value="1" selected>Soltero</option>
                 <option value="2" >Casado</option>
                 <option value="3">Divorciado</option>
                 <option value="4">Separado</option>
                 <option value="5">Unión libre</option>
                 <option value="6">Viudo</option>
                </select>
                </div>
                    
                </div>

                </div>
                    
                <div class=" flex">
                    <div class="md:flex md:items-center mb-6">
                    <label class=" px-4 block text-black  font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Trabajo: </label>
                    <input name="Trabajo" id="Trabajo" v-model="Trabajo" class=" w-96  bg-gray-100 appearance-none border-2 border-gray-200 rounded py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500" type="text" >
                </div>

                <div class="md:flex md:items-center mb-6">
                    <label class=" px-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Residencia </label>
                    <input name="Residencia" id="Residencia" v-model="Residencia" class=" w-96 bg-gray-100 appearance-none border-2 border-gray-200 rounded  py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500"  type="text" >
                </div>

                </div>

            </div><br>

            <!-- Acerca de mi  -->

                <div class="bg-blue-200 py-2 px-5 w-full text-lg ">
                    <h1 class="text-2xl font-bold text-black text-left  py-8">Parte 2.- Acerca de mi</h1>
                <div class="flex w-full">
                    <div class="md:flex md:items-center mb-6 w-6/12 ">
                    <label class=" block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Cita:</label>
                     <textarea v-model="Cita"  name="cita" id="cita" class=" text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full" rows="1"></textarea>

                    </div>
                    <div class="flex md:items-center mb-6  w-6/12">
                    
                    <label class="px-4 text-black font-bold w-36 "> Cita autor: </label>
                    
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
               


                
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Personalidad 1
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Personalidad1" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Personalidad 2
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Personalidad2" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text">
                    </div>
                </div>

                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Personalidad 3
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Personalidad3" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Personalidad 4
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Personalidad4" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Objetivos
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Objetivos" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Frustraciones
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Frustraciones" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Motivaciones
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Motivaciones" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Marcas
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Marcas" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>





                
                <div class="md:flex md:items-center">
                    <div class="md:w-1/3"></div>
                    <div class="md:w-2/3">
                        <div>
                            <button  @click="Enviar()" class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="button">
                                Enviar
                            </button>
                        </div>
                    
                    </div>
                </div>
            </form>

            </div>
            
        </div>
    </div>
</template>