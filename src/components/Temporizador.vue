<template>

    <div 
        class="is-flex is-align-items-center is-justify-content-space-between"
    >

        <Cronometro :tempoEmSegundos="tempoEmSegundos"/>

        <Botao 
            texto="play" 
            icone="fas fa-play" 
            :desabilitado="cronometroRodando"
            @clicado="iniciar"
        />

        <Botao 
            texto="stop" 
            icone="fas fa-stop" 
            :desabilitado="!cronometroRodando"
            @clicado="finalizar"
        />

    </div>
    
</template>

<script lang="ts">

    import { defineComponent } from 'vue'
    import Cronometro from './Cronometro.vue'
    import Botao from './Botao.vue'

    export default defineComponent({

        name: 'TemporizadorDeTarefas',

        emits: ['aoTemporizadorFinalizado'],

        components: {

            Cronometro,
            Botao

        },

        data () {

            return {

                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false,

            }

        },

        methods: {

            iniciar () : void {

                this.cronometro = setInterval(() => {

                    this.cronometroRodando = true
                    this.tempoEmSegundos++

                }, 1000)
                
            },

            finalizar () : void {

                //limpa o intervalo
                clearInterval(this.cronometro)
                this.cronometroRodando = false
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
                this.tempoEmSegundos = 0;


            }

        }

    })

</script>