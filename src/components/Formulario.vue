<template>
    <div class="box formulario">

        <div class="columns">

            <div 
                class="column is-8" 
                role="form" 
                aria-label="Formulário para criação de uma nova tarefa"
            >

                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa você deseja iniciar?"
                    v-model="descricao"
                >

            </div>

            <div class="column">

                <Temporizador 
                
                    @aoTemporizadorFinalizado="finalizarTarefa"

                />
                
            </div>

        </div>
        
    </div>
</template>

<script lang="ts">

    import { ITarefa } from '@/interfaces/ITarefa'
    import { defineComponent } from 'vue'
    import Temporizador from './Temporizador.vue'

    export default defineComponent({

        name: 'FormulárioDeTarefa',

        emits: ['aoSalvarTarefa'],

        components: {

            Temporizador

        },

        data () {

            return {

                descricao: '',

            }

        },

        methods: {

            finalizarTarefa (tempoDecorrido: number): void {

                const tarefa: ITarefa = {

                    duracaoEmSegundos: tempoDecorrido,
                    descricao: this.descricao

                }

                this.$emit("aoSalvarTarefa", tarefa);

                this.descricao = '';

            },

        }

})

</script>

<style>

    .formulario {

        color: var(--texto-primario);
        background-color: var(--bg-primario);

    }

</style>