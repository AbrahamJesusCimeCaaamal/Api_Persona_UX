<script>
export default {

    data() {
        return {
            slider1: 50
        }
    },
    props:{index:null},
    methods: {
        enviar() {
            this.$emit('slid', this.slider1, this.index)
        }
    }
}
</script>

<template>
    <div class="flex">
        <div class="w-full px-3">
            <slot></slot> ({{ slider1 }}%)
            <br>
            <input
                class="block w-full bg-white text-gray-700 border border-gray-200 rounded py-2 mx-auto mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 hover:tracking-wide"
                type="range" min="0" max="100" v-model="slider1" @change="enviar">
        </div>

    </div>
</template>