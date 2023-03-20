<template>

        <button 
            class="button"  
            @click="clicado"
            :disabled="desabilitado"          
        >
            <span class="icon">
                <i :class="icone" ></i>
            </span>
            <span>{{ texto }}</span>

        </button>   

</template>

<script lang="ts">

    import { defineComponent } from 'vue'

    export default defineComponent({

        name: 'BotaoDoTemporizador',
        emits: ['clicado'],
        props: {

            texto: {

                type: String,
                default: '',

            },

            icone: {

                type: String,
                default: '',

            },

            desabilitado: {

                type: Boolean,

            }

        },
        methods: {

            clicado (): void {

                this.$emit('clicado', 'Testado');

            }

        }

    })

</script>