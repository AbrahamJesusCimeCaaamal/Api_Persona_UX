<script>

export default {
    
    data() {
        return {
            slider: 50
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.slider)
        }
    }
}
</script>

<template>
    <div class="w-11/12">
        
        <input  type="range" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="Personalidad2" placeholder="" typeof="slider" min="0" max="100"  v-model="slider" @input="enviar">

    </div>
</template>