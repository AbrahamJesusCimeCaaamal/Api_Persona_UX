<script>
export default {
    
    data() {
        return {
            dato1: "",
            dato2:"",
        }
    },
    props:{index:null},
    methods: {
        enviar() {
            dato1: this.info1
            dato2: this.info2
            this.$emit('informacion',this.dato1,this.dato2,this.index)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <input type="text" v-model="dato1" name="info1" id="info1" @input="enviar"
        class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2">

        <input type="range" v-model="dato2" name="info2" id="info2" @input="enviar"
            class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2">

            {{dato2}}%
    </div>
</template>