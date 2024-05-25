<script lang="ts">
import SelecionarIngredientes from './SelecionarIngredientes.vue'; // Importa o componente SelecionarIngredientes
import SuaLista from './SuaLista.vue'; // Importa o componente SuaLista
import Tag from './Tag.vue'; // Importa o componente Tag

export default {
    name: 'ConteudoPrincipal', // Nome do componente Vue
    data() {
        return {
            ingredientes: [] as string[] // Inicializa a lista de ingredientes como um array vazio
        };
    },
    components: { SelecionarIngredientes, Tag, SuaLista }, // Registra os componentes utilizados
    methods: {
        // Método para adicionar um ingrediente à lista
        adicionarIngrediente(ingrediente: string) {
            this.ingredientes.push(ingrediente);
        },
        // Método para remover um ingrediente da lista
        removerIngrediente(ingrediente: string) {
            this.ingredientes = this.ingredientes.filter(iLista => ingrediente !== iLista);
        }
    }
}
</script>


<template>
    <main class="conteudo-principal"> <!-- Elemento principal com a classe 'conteudo-principal' -->
        <SuaLista :ingredientes="ingredientes" />
        <!-- Passa a lista de ingredientes como uma prop para o componente SuaLista -->
        <SelecionarIngredientes @adicionar-ingrediente="adicionarIngrediente($event)"
            @remover-ingrediente="removerIngrediente($event)" />
        <!-- Componente para selecionar ingredientes, que emite eventos ao adicionar e remover ingredientes -->
    </main>
</template>


<style scoped>
/* Estilos para o componente ConteudoPrincipal */
.conteudo-principal {
    padding: 6.5rem 7.5rem;
    /* Espaçamento interno */
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
        /* Ajusta o espaçamento interno */
        gap: 3.5rem;
        /* Ajusta o espaçamento entre os itens */
    }
}

@media only screen and (max-width: 767px) {
    .conteudo-principal {
        padding: 4rem 1.5rem;
        /* Ajusta o espaçamento interno */
        gap: 4rem;
        /* Ajusta o espaçamento entre os itens */
    }
}
</style>