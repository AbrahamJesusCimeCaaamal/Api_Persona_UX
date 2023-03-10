<script>
import axios from 'axios'

let API_URL = '/api/getPersonasUxd.php'

export default {

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
      <input class=" border-2 border-blue-200 rounded-full py-2 px-4" v-model="busqueda"  @input = "buscar(busqueda)"  type="text"  placeholder= "Buscar por nombre o id">
      

    </div>

    <div v-if="mosbusqueda">
      <div v-if="resultaID " class="flex mx-auto justify-center items-center space-x-4 text-base my-2"  >  
    <div class="w-3/4 mx-auto my-auto p-3 border-4 border-black bg-white rounded-sm">
      
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


        
                <h3 class="text-lg font-bold text-gray-900 sm:text-xl">
                    <strong> Nombre: </strong>{{ informacionDeUno.nombre }}
                </h3>

                <p class="mt-1 text-xs font-medium text-gray-600">Persona UX</p>
           


       

        

        
            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.edad }}</dt>
                <dd class="text-xs text-gray-500">Edad</dd>
            </div>

            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.estadoCivil }}</dt>
                <dd class="text-xs text-gray-500">Estado Civil</dd>
            </div>


            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.trabajo }}</dt>
                <dd class="text-xs text-gray-500">Trabajo</dd>
            </div>

            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.residencia }}</dt>
                <dd class="text-xs text-gray-500">Residencia</dd>
            </div>

            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.cita }}</dt>
                <dd class="text-xs text-gray-500">Cita</dd>
            </div>

            <div class="flex flex-col-reverse">
                <dt class="text-sm font-medium text-gray-600"> {{ informacionDeUno.citaAutor }}</dt>
                <dd class="text-xs text-gray-500">Autor de la Cita</dd>
            </div>

        
        <div>
            <p class="text-xs text-gray-500">Bio:
            </p>
            <p class="text-sm font-medium text-gray-600">{{ informacionDeUno.bio }}</p>
        </div>
        <div>
            <p class="text-xs text-gray-500">frustraciones:
            </p>
            <p class="text-sm font-medium text-gray-600">{{ informacionDeUno.frustaciones}}</p>
        </div>


</div>
</div>
 

 </div>





</template>