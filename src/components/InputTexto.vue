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
    <div>
        <input type="text" v-model="dato" name="info" id="info" class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2" @input="enviar">

    </div>
</template>