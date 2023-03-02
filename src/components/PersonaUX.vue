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
            Objetivos: "",
            Frustraciones: [],
            Motivaciones: [],
            Marcas: ""
        };
    },
    mounted() {
        

    },
    methods: {
        Enviar(){
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

    }
}


</script>

<template>
    <div class="flex ">
        <div class="w-full rounded-lg p-6 shadow-lg bg-white ">
            <div class=" p-2 font-bold text-xl" >
                <h1>Personalidad</h1>
            </div>
            <form class="w-full" method="get">
                <div class="md:flex mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Nombre
                    </label>
                    </div>
                    <div class="md:w-2/3">
                    <input v-model="Nombre" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Edad
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Edad" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Estado civil
                    </label>
                    </div>
                    <div class="">
                    <input v-model="EstadoCivil" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                    
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Trabajo
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Trabajo" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Residencia
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Residencia" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Cita
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Cita" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Cita autor
                    </label>
                    </div>
                    <div class="">
                    <input v-model="CitaAutor" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text">
                    </div>
                </div>
                <div class="md:flex md:items-center mb-6">
                    <div class="">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
                        Bio
                    </label>
                    </div>
                    <div class="">
                    <input v-model="Bio" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
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
                        <div @click="Enviar()">
                            <button class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="button">
                                Enviar
                            </button>
                        </div>
                    
                    </div>
                </div>
            </form>
        </div>
    </div>
</template>