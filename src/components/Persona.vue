<script>
import axios from 'axios'
import Boton from '../components/Boton_Enviar.vue';

let API_URL = '/api/getPersonasUxd.php'

export default {
  components:{

Boton,
},

  data() {
    return {
        //variables de retorno  
        //para lista de personas
        personas: [],
        
        informacionDeUno: [],
        mostrar: false,
        index:1,
    

      search:"",
      resulta:[],
      resultaID:false,
      resultaNombre:false,

      id: 0,
      infoUno:[],
      personaje: [],
      mostrar: false,
      inicio:true,
      moscarta:true,
      mosbusqueda:false,
      }
    },
    mounted() {
      axios
        .get(API_URL)
          .then((response) => {
          //paginas
          console.log (response.data.personas);
          this.info = response.data.info;
          this.personas = response.data.personas;
          
          console.log (this.personas)
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


    buscar(search)  { 
      if (search===""){
        this.moscarta = true
        this.mosbusqueda= false
      }
      else{
        this.moscarta=false
        this.mosbusqueda= true
        if(!isNaN (search) === true) {
          API_URL='/api/getPersonasUxd.php?id='+ search
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
<div >
  <!--buscador por nombre por pagina-->
  <div class="flex justify-align-center mx-auto  my-5 ">
      
      <h3 class="text-2xl text-center  mx-5 sm:py-2"> <strong>Buscar  </strong></h3>
      <input class=" border-2 border-blue-200 rounded-full py-2 px-4" v-model="busqueda"  @input = "buscar(busqueda)"  type="text"  placeholder= "Buscar id">
      

    </div>

    <div v-if="mosbusqueda">
      <div v-if="resultaID " class="flex mx-auto justify-center items-center space-x-4 text-base my-2"  >  
    <div class="w-3/6 mx-auto my-auto p-3 border-4 border-black bg-white rounded-sm">
      
      <div class="info-buscados text-xl">
        <h2> <strong>Id:</strong>  {{ resulta.id }}</h2>
        <h2> <strong>  Nombre:</strong> {{ resulta.nombre}}</h2>
    
      </div>
    </div>      
  </div>


     </div>

    
</div >
  

 <div v-if="moscarta" class=" grid grid-cols-2 text-left w-full">


    <!--Recorre la nueva lista y por cada personaje que encuentra-->    
<div  class=" w-4/5 sm:px-2 lg:px-8  border-2 border-black bg-lime-100 rounded-sm">
      
      <div class="text-2xl my-10 text-black sm:text-base  sm:py-2" >
          <h1 class="text-3xl text-center font-bold" > Lista de Personas</h1><br>
          <ul class="text-xl py-2">
            <li v-for="(p,index = 1) in personas">
              <!--Llamando función obtener info personal por personaje-->
              <button class="hover:underline hover:text-blue-700" @click="InfoPersona(p.id)"> {{ index += 1 }}. {{ p.nombre }} </button> 
              
            </li>
          </ul>
        </div>
        
  </div>




 
 <div v-if="mostrar">

<div class="personaje w-full sm:px-2 lg:px-8  border-2 border-black bg-lime-100 rounded-sm">

  <p class=" text-center mt-1 text-2xl font-bold text-black">Persona UX</p>
        
                <h3 class="text-lg text-black py-2 ">
                    <strong> Nombre: </strong> {{ informacionDeUno.nombre }}
                </h3>

            
                <h3 class="text-base text-black py-2 ">
                    <strong> Edad: </strong> {{ informacionDeUno.edad  }}
                </h3>
              
                <h3 class="text-base text-black py-2 ">
                    <strong> Estad Civil: </strong> {{ informacionDeUno.estadoCivil   }}
                </h3>
                <h3 class="text-base text-black py-2 ">
                    <strong> Trabajo: </strong> {{ informacionDeUno.trabajo  }}
                </h3>
                <h3 class="text-base text-black py-2 ">
                    <strong> Recidencia: </strong> {{ informacionDeUno.residencia  }}
                </h3>
                <h3 class="text-base text-black py-2 ">
                    <strong> Cita: </strong> {{ informacionDeUno.cita  }}
                </h3>
                <h3 class="text-base text-black py-2 ">
                    <strong> Autor de la Cita: </strong> {{ informacionDeUno.citaAutor  }}
                </h3>
        
        
            <p class="text-base font-bold text-black">Bio:
            </p>
            <p   class="text-base  text-black">{{ informacionDeUno.bio }}</p>
        
<div >
  <h1 class=" py-2 text-center text-2xl font-semibold">Objetivos</h1>
  <div class=" bg-orange-200 w-full mt-4 mx-auto px-3" v-for="o,index in informacionDeUno.objetivos">
            <label class=" text-black font-bold md:text-left my-2 md:mb-0">
                Objetivo {{ index +1 }}
                <br>
            </label>
            <h4 class="mb-1 px-3"> {{ o.objetivo}}</h4>
          </div>
</div>

        
        
          <div>
            <h1 class=" py-2 text-center text-2xl font-semibold">Frustraciones</h1>
            <div class=" bg-blue-200 w-full mt-4 mx-auto px-3" v-for="f,index2 in informacionDeUno.frustraciones">
            <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">frustración {{index2+1}} </h1>
            <h1 class="text-base  mb-1 px-3  text-black" >  {{ f.frustracion }}</h1> 
          </div>
          </div>

          <div>
            <h1 class=" py-2 text-center text-2xl font-semibold">Motivaciones</h1>
            <div class=" bg-yellow-200 w-full mt-4 mx-auto px-3" v-for="f,index2 in informacionDeUno.motivaciones">
            <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">Motivación {{index2+1}} </h1>
            <h1 class="text-base  mb-1 px-3  text-black" >  {{ f.motivacion }}  {{ f.porcentaje}}%</h1> 
          </div>
          </div>

          <div>
            <h1 class=" py-2 text-center text-2xl font-semibold">Motivaciones</h1>
            <div class=" bg-rose-200 w-full mt-4 mx-auto px-3" v-for="f,index2 in informacionDeUno.marcas">
            <h1 class=" text-black font-bold md:text-left my-2 md:mb-0">Motivación {{index2+1}} </h1>
            <h1 class="text-base  mb-1 px-3  text-black" >  {{ f.marca }}</h1> 
          </div>
          </div>


         
       


</div>
</div>
 

 </div>





</template>