<script lang="ts">
import MostrarReceitas from './MostrarReceitas.vue';
import SelecionarIngredientes from './SelecionarIngredientes.vue'; // Importa o componente SelecionarIngredientes
import SuaLista from './SuaLista.vue';
import Tag from './Tag.vue'; // Importa o componente Tag

type Pagina = 'SelecionarIngrediente' | 'MostrarReceitas';

export default {
    name: 'ConteudoPrincipal', // Nome do componente Vue
    data() {
        return {
            ingredientes: [] as string[], // Dados do componente: uma lista de ingredientes
            conteudo: 'SelecionarIngrediente' as Pagina
        };
    },
    components: { SelecionarIngredientes, Tag, SuaLista, MostrarReceitas }, // Registra os componentes SelecionarIngredientes e Tag
    methods: {
        adicionarIngrediente(ingrediente: string) {
            this.ingredientes.push(ingrediente)
        },

        removerIngrediente(ingrediente: string) {
            this.ingredientes = this.ingredientes.filter(iLista => ingrediente !== iLista);
        },

        navegar(pagina: Pagina) {
            this.conteudo = pagina;
        }
    }
}
</script>


<template>
    <main class="conteudo-principal"> <!-- Elemento principal com a classe 'conteudo-principal' -->
        <SuaLista 
            :ingredientes="ingredientes" 
            v-if="conteudo === 'SelecionarIngrediente'"/>
            
        <!-- Componente SelecionarIngredientes para seleção de ingredientes -->
        <SelecionarIngredientes 
            v-if="conteudo === 'SelecionarIngrediente'"
            @adicionar-ingrediente="adicionarIngrediente($event)" 
            @remover-ingrediente="removerIngrediente($event)"
            @MostrarReceitas="navegar('MostrarReceitas')" />

        <MostrarReceitas 
            v-else-if="conteudo === 'MostrarReceitas'" 
            />
    </main>
</template>



<style scoped>
.conteudo-principal {
    padding: 6.5rem 7.5rem;
    /* Espaçamento interno (padding) */
    border-radius: 3.75rem 3.75rem 0rem 0rem;
    /* Bordas arredondadas */
    background: var(--creme, #FFFAF3);
    /* Cor de fundo */
    color: var(--cinza, #444);
    /* Cor do texto */

    display: flex;
    /* Define como flexbox */
    flex-direction: column;
    /* Orienta os itens em coluna */
    align-items: center;
    /* Alinha os itens ao centro */
    gap: 5rem;
    /* Espaço entre os itens */
}

/* Estilos responsivos para telas menores */
@media only screen and (max-width: 1300px) {
    .conteudo-principal {
        padding: 5rem 3.75rem;
        /* Ajusta o espaçamento interno (padding) */
        gap: 3.5rem;
        /* Ajusta o espaçamento entre os itens */
    }
}

@media only screen and (max-width: 767px) {
    .conteudo-principal {
        padding: 4rem 1.5rem;
        /* Ajusta o espaçamento interno (padding) */
        gap: 4rem;
        /* Ajusta o espaçamento entre os itens */
    }
}
</style>