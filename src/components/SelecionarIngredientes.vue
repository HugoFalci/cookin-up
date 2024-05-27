<script lang="ts">
import { obterCategorias } from '@/http/index'; // Importa a função obterCategorias do arquivo index.ts em '@/http/'
import type ICategoria from '@/interfaces/ICategoria'; // Importa a interface ICategoria
import CardCategoria from './CardCategoria.vue'; // Importa o componente CardCategoria
import BotaoPrincipal from './BotaoPrincipal.vue';

export default {
    data() {
        return {
            categorias: [] as ICategoria[] // Inicializa um array vazio para armazenar as categorias
        }
    },

    async created() {
        this.categorias = await obterCategorias(); // Carrega as categorias ao criar o componente
    },

    components: { CardCategoria, BotaoPrincipal }, // Registra o componente CardCategoria
    emits: ['adicionarIngrediente', 'removerIngrediente']
}
</script>



<template>
    <section class="selecionar-ingredientes">
        <!-- Título "ingredientes" -->
        <h1 class="cabecalho titulo-ingredientes">ingredientes</h1>

        <!-- Descrição para selecionar ingredientes -->
        <p class="paragrafo titulo-ingredientes">
            Selecione abaixo os ingredientes que você quer usar nesta receita:
        </p>

        <!-- Lista de categorias -->
        <ul class="categorias">
            <!-- Itera sobre as categorias e exibe um CardCategoria para cada uma -->
            <li v-for="categoria in categorias" :key="categoria.nome">
                <CardCategoria :categoria="categoria" @adicionar-ingrediente="$emit('adicionarIngrediente', $event)" @remover-ingrediente="$emit('removerIngrediente', $event)"/>
            </li>
        </ul>

        <!-- Dica para os ingredientes básicos -->
        <p class="paragrafo dica">
            *Atenção: consideramos que você tem em casa: sal, pimenta e água.
        </p>
        
        <BotaoPrincipal texto="Buscar Ingrediente"/>
    </section>
</template>


<style scoped>
/* Estilo para a classe 'selecionar-ingredientes' */
.selecionar-ingredientes {
    display: flex;
    /* Define como flexbox */
    flex-direction: column;
    /* Itens dispostos em coluna */
    align-items: center;
    /* Itens centralizados verticalmente */
}

/* Estilo para o título "ingredientes" */
.titulo-ingredientes {
    color: var(--verde-medio, #3D6D4A);
    /* Cor do texto verde médio */
    display: block;
    /* Exibe como bloco */
    margin-bottom: 1.5rem;
    /* Margem inferior */
}

/* Estilo para as instruções */
.instrucoes {
    margin-bottom: 2rem;
    /* Margem inferior */
}

/* Estilo para a lista de categorias */
.categorias {
    margin-bottom: 1rem;
    /* Margem inferior */
    display: flex;
    /* Define como flexbox */
    justify-content: center;
    /* Itens centralizados horizontalmente */
    gap: 1.5rem;
    /* Espaçamento entre os itens */
    flex-wrap: wrap;
    /* Permite que os itens quebrem para a próxima linha */
}

/* Estilo para a dica */
.dica {
    align-self: flex-start;
    /* Alinha à esquerda */
    margin-bottom: 3.5rem;
    /* Margem inferior */

}

/* Estilos responsivos para telas com largura máxima de 767px */
@media only screen and (max-width: 767px) {
    .dica {
        margin-bottom: 2.5rem;
        /* Ajusta a margem inferior */
    }
}
</style>
