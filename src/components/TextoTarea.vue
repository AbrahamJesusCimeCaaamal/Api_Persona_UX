<script>

export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            
            this.$emit('dato',this.dato)
        }
    }
}
</script>

<template>
        <textarea type="text" v-model="dato" name="dato" id="dato" class="text-secundario font-semibold font-contenido px-5 py-3 border-2 border-secundario w-full "  rows="2" @input="enviar"></textarea>    

</template>