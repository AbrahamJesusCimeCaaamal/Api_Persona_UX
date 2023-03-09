<script>


export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            
            this.$emit('datoTexto',this.dato)
        }
    }
}
</script>

<template>
         
        <textarea type="text" v-model="dato" name="Bio" id="Bio" class="text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full"  rows="4" @input="enviar"></textarea>
</template>