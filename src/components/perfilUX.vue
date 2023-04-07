<script>
import axios from 'axios'
import Boton from '../components/Boton_Enviar.vue';

let API_URL = '/api/getPersonasUxd.php'

export default {
    components: {

        Boton,
    },

    data() {
        return {
            //variables de retorno  
            //para lista de personas
            personas: [],

            informacionDeUno: [],
            mostrar: false,
            index: 1,


            search: "",
            resulta: [],
            resultaID: false,
            resultaNombre: false,

            id: 0,
            infoUno: [],
            personaje: [],
            mostrar: false,
            inicio: true,
            moscarta: true,
            mosbusqueda: false,
        }
    },
    mounted() {
        axios
            .get(API_URL)
            .then((response) => {
                //paginas
                console.log(response.data.personas);
                this.info = response.data.info;
                this.personas = response.data.personas;

                console.log(this.personas)
                console.log(this.info)
            })
    },

    methods: {
        InfoPersona(id) {

            //url de consumo API
            API_URL = '/api/getPersonasUxd.php?id=' + id
            console.log(API_URL)
            //lo obtiene
            axios.get(API_URL)
                //
                .then((response) => {
                    console.log(response) //regresa datos de un solo personaje
                    //contiene el array de cada personaje con sus datos
                    this.informacionDeUno = response.data.persona;
                    console.log(this.informacionDeUno)
                })
            //this.id++
            this.mostrar = true
            console.log(this.mostrar)
        },
        enviarDato() {
            this.$emit(this.search);
        },


        buscar(search) {
            if (search === "") {
                this.moscarta = true
                this.mosbusqueda = false
            }
            else {
                this.moscarta = false
                this.mosbusqueda = true
                if (!isNaN(search) === true) {
                    API_URL = '/api/getPersonasUxd.php?id=' + search
                    axios.get(API_URL)
                        .then((response) => {
                            console.log(response.data.persona)
                            this.resulta = response.data.persona;
                            console.log(this.resulta)
                        })
                    this.resultaID = true
                    this.resultaNombre = false
                }


            }
        }

    },
}
</script>

<template>
    <div class="h-full">
        <!--buscador por nombre por pagina-->
        <div class="flex justify-align-center mx-auto  my-5 ">

            <h3 class="text-2xl text-center  mx-5 sm:py-2"> <strong>Buscar </strong></h3>
            <input class=" border-2 border-blue-200 rounded-full py-2 px-4" v-model="busqueda" @input="buscar(busqueda)"
                type="text" placeholder="Buscar id">


        </div>

        <div v-if="mosbusqueda">
            <div v-if="resultaID" class="flex mx-auto justify-center items-center  text-base my-2">
                <div class="w-full  my-auto border-4 border-black bg-white rounded-sm">

                    <div class="info-buscados text-xl">
                        <div class="personaje w-full  ">

                            <div class="bg-blue-500">
                                <h1 class="text-4xl font-medium text-white py-2 px-8 ">
                                    {{ resulta.nombre }}
                                </h1>
                            </div>

                            <div class="grid grid-cols-3  ">
                                <div>

                                    <div class="px-8 py-1">
                                        <h3 class="text-xl text-black py-1 ">
                                            <strong> Edad: </strong> {{ resulta.edad }}
                                        </h3>

                                        <h3 class="text-xl text-black py-1 ">
                                            <strong> Estad Civil: </strong> {{ resulta.estadoCivil }}
                                        </h3>
                                        <h3 class="text-xl text-black py-1 ">
                                            <strong> Trabajo: </strong> {{ resulta.trabajo }}
                                        </h3>
                                        <h3 class="text-xl text-black py-1 ">
                                            <strong> Recidencia: </strong> {{ resulta.residencia }}
                                        </h3>
                                       

                                    </div>
                                    <div class="px-4 mb-2">
                                        <p class=" text-2xl  text-center font-bold text-black">Bio:
                                    </p>
                                    <p class=" text-xl  text-black">{{ resulta.bio }}</p>

                                    </div>
                                    <div class="px-28 mb-3"><img class="  scale-100 " src="../components/icons/perfilux.jpg"
                                            width="300" height="300">
                                    </div>

                                    <div class=" px-4   ">
                                        <div class="bg-blue-400">
                                            <h3 class="text-xl text-black py-1 px-2 ">
                                                <strong> Cita: </strong> {{ resulta.cita }}
                                            </h3>
                                            <h3 class="text-xl text-black py-2 px-2 ">
                                                <strong> Autor de la Cita: </strong> {{ resulta.citaAutor }}
                                            </h3>
                                        </div>
                                    </div>



                                </div>


                                <div>



                                    


                                    <div class="px-4 text-xl">
                                        <div>
                                            <h1 class=" py-2 text-center text-2xl font-semibold">Motivaciones</h1>
                                            <div class=" bg-yellow-200 w-full mt-4 mx-auto px-3"
                                                v-for="f, index2 in resulta.motivaciones">
                                                <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">Motivación {{
                                                    index2 + 1 }}
                                                </h1>
                                                <h1 class="text-xl mb-1 px-3  text-black"> {{ f.motivacion }} {{
                                                    f.porcentaje }}%
                                                    <input type="range" v-model="f.porcentaje" name="info2" id="info2"
                                                        @input="enviar"
                                                        class="   px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-8/12" disabled
                                                        placeholder="" typeof="slider" min="0" max="100">


                                                </h1>
                                            </div>
                                        </div>

                                    </div>









                                    <div>
                                        <h1 class=" py-2 text-center text-2xl font-semibold">Personalidad</h1>

                                            <div class="px-4 mb-3 ">
                                                <div class="bg-purple-200 px-2 text-xl py-2">
                                                <h1 class="font-bold">Personalidad 1: Mente</h1>
                                            <div class=" sm:px-1 md:flex">
                                                <h1 class="px-2">Extrovertido {{ resulta.personalidad01 }}% </h1>

                                                <input type="range" v-model="resulta.personalidad01" name="info2" id="info2"
                                                    @input="enviar" class="  px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-10/12"
                                                    disabled placeholder="" typeof="slider" min="0" max="100">


                                                <h1> Introvertido {{ 100 - resulta.personalidad01 }}% </h1>

                                            </div>
                                            </div>
                                            </div>


                                            <div class="px-4 mb-3">
                                                <div class="bg-purple-200 px-2 text-xl py-2">
                                                    <h1 class="font-bold">Personalidad 2: Enería</h1>
                                            <div class=" sm:px-1 md:flex">
                                                <h1 class="px-2">Intuitivo {{ resulta.personalidad02 }}% </h1>

                                                <input type="range" v-model="resulta.personalidad02" name="info2" id="info2"
                                                    @input="enviar" class="  px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-10/12"
                                                    disabled placeholder="" typeof="slider" min="0" max="100">


                                                <h1> Observador {{ 100 - resulta.personalidad02 }}% </h1>

                                            </div>
                                                </div>
                                            </div>





                                            <div class="px-4 mb-3">
                                                <div class="bg-purple-200 px-2 text-xl py-2">
                                                    <h1 class="font-bold">Personalidad 3: Naturaleza</h1>
                                            <div class=" sm:px-1 md:flex">
                                                <h1 class="px-2">Pensamiento {{ resulta.personalidad03 }}% </h1>

                                                <input type="range" v-model="resulta.personalidad03" name="info2" id="info2"
                                                    @input="enviar" class="  px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-10/12"
                                                    disabled placeholder="" typeof="slider" min="0" max="100">


                                                <h1> Emocional {{ 100 - resulta.personalidad03 }}% </h1>

                                            </div>
                                                </div>
                                            </div>



                                            <div class="px-4 mb-3">
                                                <div class="bg-purple-200 px-2 text-xl py-2">
                                                    <h1 class="font-bold">Personalidad 4: Identidad</h1>
                                            <div class=" sm:px-1 md:flex">
                                                <h1 class="px-2">Asertivo {{ resulta.personalidad04 }}% </h1>

                                                <input type="range" v-model="resulta.personalidad04" name="info2" id="info2"
                                                    @input="enviar" class="  px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-10/12"
                                                    disabled placeholder="" typeof="slider" min="0" max="100">


                                                <h1> Cauteloso {{ 100 - resulta.personalidad04 }}% </h1>

                                            </div>
                                                </div>
                                            </div>

                                    </div>


                                </div>











                                <div>

                                    <div>
                                        <h1 class=" py-2 text-center text-2xl font-semibold">Objetivos</h1>
                                        <div class=" bg-orange-200 w-full mt-4 mx-auto px-3"
                                            v-for="o, index in resulta.objetivos">
                                            <label class=" text-black font-bold md:text-left my-2 md:mb-0">
                                                Objetivo {{ index + 1 }}
                                                <br>
                                            </label>
                                            <h4 class="mb-1 px-3 text-xl"> {{ o.objetivo }}</h4>
                                        </div>
                                    </div>



                                    <div>
                                        <h1 class=" py-2 text-center text-2xl font-semibold">Frustraciones</h1>
                                        <div class=" bg-blue-200 w-full mt-4 mx-auto px-3"
                                            v-for="f, index2 in resulta.frustraciones">
                                            <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">frustración {{
                                                index2 + 1 }}
                                            </h1>
                                            <h1 class="text-base  mb-1 px-3  px-3 text-xl text-black"> {{ f.frustracion }}</h1>
                                        </div>
                                    </div>


                                    <div>
                                        <h1 class=" py-2 text-center text-2xl font-semibold">Marcas</h1>
                                        <div class=" bg-rose-200 w-full mt-4 mx-auto px-3"
                                            v-for="f, index2 in resulta.marcas">
                                            <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">Marca {{ index2 + 1
                                            }}
                                            </h1>
                                            <h1 class=" px-3 text-xl mb-1 px-3  text-black"> {{ f.marca }}</h1>
                                        </div>
                                    </div>
                                </div>

                            </div>




















































                        </div>

                    </div>
                </div>
            </div>


        </div>


    </div>


    <div v-if="moscarta" class=" px-8 text-center bg-red-300">
        <h1 class="text-2xl font-bold"> Método de uso</h1> <br>
        <p class="text-xl font-medium">Ingrese un id para realizar una búsqueda y le aparecerá el formato con el perfil del
            usuario</p>
        <br>
    <div class="grid grid-cols-3 divide-x">
        <div></div>
        <div><img class="scale-150 py-16 " src="../components/icons/perfil.png" width="500" height="500">
        </div>
        <div></div>

    </div><br>



</div><br></template>