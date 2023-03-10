<script>
export default {
    
    data() {
        return {
            dato: "",
            dato2: "",
        }
    },
    props:{index:null,index2:null},
    methods: {
        enviar() {
            
            this.$emit('infor1',this.dato, this.index)
        },
        enviar2() {
            
            this.$emit('infor2', this.dato2,this.index2)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
            <input  type="text" v-model ="dato" name="info" id="info" @input="enviar" class=" placeholder:motivacion block w-full bg-white text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 hover:tracking-wide">
            <input  type="text" v-model ="dato2" name="info2" id="info" @input="enviar2" class=" placeholder:motivacion block w-full bg-white text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 hover:tracking-wide">
        
            </div>
</template>