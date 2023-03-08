<script>

export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            
            this.$emit('info',this.dato)
        }
    }
}
</script>

<template>
    <div class=" w-1/2">
        <input type="text" v-model="dato" name="info" id="info" class=" 2xl:w-80 sm:w-60  md:w-80  h-10 bg-while  appearance-none border-2 border-gray-200 rounded  py-2 px-4 text-gray-700 leading-tight focus:outline-none  focus:ring-blue-500 focus:border-blue-500"  @input="enviar">

    </div>
</template>