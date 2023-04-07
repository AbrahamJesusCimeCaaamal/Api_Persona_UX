<script>
export default {
    
    data() {
        return {
            dato1: "",
            dato2:50,
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

        <input type="range" v-model="dato2" name="info2" id="info2" @input="enviar"
            class=" px-2 py-1 rounded-lg mb-3 ml-2 mr-2 w-10/12"  placeholder="" typeof="slider" min="0" max="100"  >{{dato2}}%

    </div>
</template>