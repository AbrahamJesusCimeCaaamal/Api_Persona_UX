<script>
import Boton from '../components/Boton_Enviar.vue';
import slider from '../components/InputSliders.vue';
import inputtext from '../components/InputTexto.vue';
import TextoTarea from '../components/TextoTarea.vue';
import textoArea  from '../components/TextAreaAmplia.vue';
import inputArray from '../components/inputArray.vue';
import frust from '../components/InputFrus.vue'
import slider1 from '../components/sliderM.vue';

import axios from 'axios';
export default {
  components:{

    Boton,slider,inputtext,TextoTarea,textoArea,inputArray,frust,slider1
  },
  emits: ['person','info','dato','datoTexto','informa','infor','infor2','informacion'] , 



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

            ValorObjetivos: "",
            Objetivos: [{value:''}],

            ValorFrustracion: "",
            Frustraciones: [{value:''}],

            valores: "",
            Motivaciones: [{ value: '', 'porcentaje': '' }],

            
            Marcas: "",
            
            
            
        };
    },
    mounted() {
        

    },
    methods: {
      
    MotivacionesVal(s,m, index) {
      this.Motivaciones[index] = {value: s,porcentaje: m}
      console.log(this.Motivaciones)
      
    },

     objetivosValores(s, index){
      this.Objetivos[index] = {value: s}
      console.log(this.Objetivos)
    },
    metodoFrustracion(s, index){
      this.Frustraciones[index] = {value: s}
      console.log(this.Frustraciones)
    },
      texto3(y){
                this.Bio=y;

            },
      texto1(t){
                this.Cita=t;

            },
      texto2(t){
                this.CitaAutor=t;

            },
      info1(a){
                this.Nombre=a;

            },
      info2(a){
                this.Edad=a;

            },
      info3(a){
                this.Trabajo =a;

            },

      info4(a){
                this.Residencia =a;

            },
      
      
      pers1(s){
                this.Personalidad1=s;

            }
      ,
      pers2(s){
                this.Personalidad2=s;

            }
      ,
      pers3(s){
                this.Personalidad3=s;

            }
      ,
      pers4(s){
                this.Personalidad4=s;

            }
      ,
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
            if (this.Bio.length < 701 && this.Bio != "" ){
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


                    <inputtext @info= " info1 " > Nombre</inputtext>


                    
                </div>
                <div class="md:flex md:items-center mb-6">
                    
                    <label class=" px-6 block font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Edad:</label>
                    <inputtext @info= " info2 " > Edad</inputtext>
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
                    <inputtext @info= " info3 " > Trabajo</inputtext>
                  </div>

                <div class="md:flex md:items-center mb-6">
                    <label class=" px-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Residencia </label>
                    <inputtext @info= " info4 " > Recidencia</inputtext>
                  </div>

                </div>

            </div><br>

            <!-- Acerca de mi  -->

                <div class="bg-blue-200 py-2 px-5 w-full text-lg ">
                    <h1 class="text-3xl font-bold text-black  py-8">Acerca de mi</h1>
                <div class="lg:flex w-full">
                    <div class="md:flex md:items-center mb-6 lg:w-6/12 sm:w-full ">
                    <label class=" block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Cita:</label>
                     
                    <TextoTarea @dato= "texto1" > Cita</TextoTarea>
                    
                    

                    </div>
                    <div class="md:flex md:items-center mb-6  lg:w-6/12 sm:w-full ">
                    
                    <label class="px-2  text-black font-bold w-32   sm:w-44 "> Cita autor: </label>
                    
                    <div class="w-11/12 ">
                     <TextoTarea @dato= "texto2" > CitaAutor</TextoTarea>
                    </div>
                </div>
                </div>



                <div class="md:flex md:items-center mb-6">
                    
                    <label class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name"> Bio: </label>
                    
                    <div class="w-full">
                      <TextoTarea @dato= "texto3" > CitaAutor</TextoTarea>
                    
                      </div>
                    
                </div>
                </div>
                <br>
               

<!--- Personalidades, division de cada personalidad por invididual -->
<div class="  bg-rose-200 px-4 py-8">
 <h1 class=" text-3xl font-bold">Personalidad</h1>
  <div class="w-full mt-4">
          <div class="md:px-8 px-2 text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 1.- Mente
          </label><br>
          <div class=" sm:px-1 md:flex">
          <h1 class="px-2">Extrovertido  {{ this.Personalidad1 }}% </h1>
          
          <slider @person="pers1">Personalidad 01</slider>
          
          <h1> Introvertido {{100- this.Personalidad1 }}% </h1>
          
        </div>

          </div>

  </div>
        


  <div class="w-full mt-4">
          <div class="md:px-8 px-2  text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 2.- Energía
          </label><br>

          <div class="md:flex">
          <h1 class="px-2">Intuitivo  {{ this.Personalidad2 }}% </h1>
          <slider @person="pers2">Personalidad 02</slider>
            <h1> Observador {{100- this.Personalidad2 }}% </h1>
          
        </div>

          </div>

  </div>

  <div class="w-full mt-4">
          <div class="md:px-8 px-2  text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 3.-Naturaleza
          </label><br>

          <div class="md:flex">
          <h1 class="px-2">Pensamiento  {{ this.Personalidad3 }}% </h1>
          <slider @person="pers3">Personalidad 03</slider> 
         <h1> Emocional {{100- this.Personalidad3 }}% </h1>
          
        </div>


          </div>

  </div>

  <div class="w-full mt-4">
          <div class="md:px-8 px-2  text-lg bg-red-100  border-2 border-indigo-500/100  ">
            <label class="block text-black font-bold md:text-left my-2 md:mb-0">
            Personalidad 4.- Identidad
          </label><br>

          <div class="md:flex">
          <h1 class="px-2">Asertivo {{ this.Personalidad4 }}% </h1>
          <slider @person="pers4">Personalidad 04</slider>
          <h1> Cauteloso {{100- this.Personalidad4 }}% </h1>
          
        </div>

          </div>

  </div>
      




</div><br>

   <div class="bg-green-200 sm:px-4 lg:px-60 md:px-40  py-4" >
    <h1 class="text-3xl font-bold">Complementos</h1><br>
  
    
    <div class="text-left items-center mb-6 sm:w-full  px-2 py-2 bg-orange-300">
      <label  class=" py-2 block text-black-500 font-bold mb-2 md:mb-0 pr-4" for="inline-full-name">  Objetivos: </label> 
      <div class="px-3 py-1 " v-for="(obj, index) in Objetivos">
      <inputArray @informa="objetivosValores"  :index="index"> </inputArray>
      </div>
        <div class="xl:px-28 sm:px-2 md:px-4 lg:px-16  2xl:96      ">
          
          <button class="bg-purple-300 text-lg px-2 py-1 border-2 border-blue-500 rounded-md " v-on:click.prevent="this.Objetivos.push(ValorObjetivos)">Nuevo </button> 
    
        </div>
         
       
    </div>






    <div class="text-left mb-6  sm:w-full px-2 py-2 bg-orange-300">
      <label class="py-2 block text-black font-bold mb-1 md:mb-0 pr-4" for="inline-full-name">Frustraciones:</label>
      <div class="px-3 py-2 " v-for="(frus, index) in Frustraciones">
        <inputArray @informa="metodoFrustracion"  :index="index"> </inputArray>  
      </div>
      <div class='xl:px-28 sm:px-2 md:md:px-4  lg:px-16  2xl:96  '>
        <button class="  bg-purple-300 text-lg px-2 py-1 border-2 border-blue-500 rounded-md "  v-on:click.prevent="this.Frustraciones.push(ValorFrustracion)">Nuevo </button> 
  
      </div>
      
    </div>
    <div class="w-full px-3 block">
            <labelView>Motivaciones:</labelView>
            <div v-for="(obj, index) in Motivaciones">
                  <slider1 @informacion=" MotivacionesVal" :index="index"> </slider1>
                
                </div>
                <button v-on:click.prevent="this.Motivaciones.push(valores)" class="px-4 py-2 mb-2 bg-gray-600 text-white rounded"> Agregar</button>
              
          </div>


    <div class="text-left items-center mb-6 sm:w-full  px-2 py-2 bg-orange-300">
      <div class="flex mb-6 lg:w-4/5  sm:w-full  px-2 py-2">
      <label class="py-4 block text-black font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">Marcas: </label>  
      <input v-model="Marcas" class="bg-while appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" >
                     
    </div>
    </div>
    

   </div>             

    <div class=" py-2">
                    
          <Boton @click="Enviar()" class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="button">
            Enviar
          </Boton>

                    
    </div>
            </form>

            </div>
            
        </div>
    </div>
</template>