<template>
    <header>
        <h1>

            <img src="../assets/logo.png" alt="">

        </h1>

        <button class="button" @click="alterarTema">
            <i 
                :class="{ 'fa-sharp fa-solid fa-moon': !modoEscuroAtivo ,'fa-sharp fa-solid fa-sun': modoEscuroAtivo }"
            ></i>
            {{ textoBotao }}
        </button>
    </header>
</template>

<script lang="ts">

    import { defineComponent } from 'vue';

    export default defineComponent({

        name: "BarraLateral",
        emits: ["aoTemaAlterado"],
        data () {

            return {

                modoEscuroAtivo: false

            }

        },
        computed: {

            textoBotao () {

                if (this.modoEscuroAtivo) {

                    return 'Desativar modo escuro'

                }

                return 'Ativar modo escuro'

            }

        },
        methods: {

            alterarTema () {

                this.modoEscuroAtivo = !this.modoEscuroAtivo
                this.$emit("aoTemaAlterado", this.modoEscuroAtivo)

            }

        }

    });

</script>

<style scoped>

    header {

        padding: 1rem;
        background-color: #0D3B66;
        width: 100%;
        height: 100vh;
        text-align: center;

    }

    header i {

        margin-right: 20px;

    }

    @media only screen and (max-width: 768px) {

        header {

            padding: 2.5rem;
            height: auto;

        }

    }

</style>