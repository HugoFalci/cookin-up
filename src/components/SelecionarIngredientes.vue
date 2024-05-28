<script lang="ts">
// Importações necessárias
import { obterCategorias } from '@/http/index'; // Importa a função obterCategorias do arquivo index.ts em '@/http/'
import type ICategoria from '@/interfaces/ICategoria'; // Importa a interface ICategoria
import CardCategoria from './CardCategoria.vue'; // Importa o componente CardCategoria
import BotaoPrincipal from './BotaoPrincipal.vue'; // Importa o componente BotaoPrincipal

// Exporta o componente Vue
export default {
    name: 'SelecionarIngredientes',
    // Declaração dos dados do componente
    data() {
        return {
            categorias: [] as ICategoria[] // Inicializa um array vazio para armazenar as categorias
        }
    },

    // Método executado ao criar o componente
    async created() {
        this.categorias = await obterCategorias(); // Carrega as categorias ao criar o componente
    },

    // Registro dos componentes utilizados neste componente
    components: { CardCategoria, BotaoPrincipal }, // Registra os componentes CardCategoria e BotaoPrincipal

    // Declaração dos eventos emitidos pelo componente
    emits: ['adicionarIngrediente', 'removerIngrediente', 'MostrarReceitas']
}
</script>


<template>
    <!-- Seção para selecionar ingredientes -->
    <section class="selecionar-ingredientes">
        <!-- Título "ingredientes" -->
        <h1 class="cabecalho titulo-ingredientes">ingredientes</h1>

        <!-- Descrição para selecionar ingredientes -->
        <p class="paragrafo titulo-ingredientes">
            Selecione abaixo os ingredientes que você quer usar nesta receita:
        </p>

        <!-- Lista de categorias -->
        <ul class="categorias">
            <!-- Iteração sobre as categorias e exibição de um CardCategoria para cada uma -->
            <li v-for="categoria in categorias" :key="categoria.nome">
                <CardCategoria 
                    :categoria="categoria" 
                    @adicionar-ingrediente="$emit('adicionarIngrediente', $event)"
                    @remover-ingrediente="$emit('removerIngrediente', $event)" />
            </li>
        </ul>

        <!-- Dica para os ingredientes básicos -->
        <p class="paragrafo dica">
            *Atenção: consideramos que você tem em casa: sal, pimenta e água.
        </p>

        <!-- Botão principal -->
        <BotaoPrincipal 
            texto="Buscar Ingrediente" 
            @click="$emit('MostrarReceitas')"/>
    </section>
</template>


<style scoped>
/* Estilos CSS para o componente */

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