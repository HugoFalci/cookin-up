<script lang="ts">
import type ICategoria from '@/interfaces/ICategoria'; // Importa a interface ICategoria para tipagem
import type { PropType } from 'vue'; // Importa PropType para tipagem de propriedades do Vue
import Tag from '@/components/Tag.vue'; // Importa o componente Tag
import IngredienteSelecionado from './IngredienteSelecionado.vue';

export default {
    props: {
        // Define a propriedade 'categoria' que é do tipo ICategoria e é obrigatória
        categoria: { type: Object as PropType<ICategoria>, required: true }
    },

    components: { Tag, IngredienteSelecionado }, // Registra o componente Tag para uso dentro deste componente

    emits: ['adicionarIngrediente', 'removerIngrediente']
}
</script>


<template>
    <!-- Estrutura do artigo com a classe 'categoria' -->
    <article class="categoria">
        <!-- Cabeçalho do artigo com a classe 'categoria__cabecalho' -->
        <header class="categoria__cabecalho">
            <!-- Imagem da categoria -->
            <img :src="`/imagens/icones/categorias_ingredientes/${categoria.imagem}`" alt="" class="categoria__imagem">

            <!-- Nome da categoria -->
            <h2 class="paragrafo-lg categoria__nome">{{ categoria.nome }}</h2>
        </header>

        <!-- Lista de ingredientes da categoria -->
        <ul class="categoria__ingredientes">
            <!-- Itera sobre os ingredientes da categoria e renderiza um componente Tag para cada um -->
            <li v-for="ingrediente in categoria.ingredientes" :key="ingrediente">
                <IngredienteSelecionado :ingrediente="ingrediente"
                    @adicionar-ingrediente="$emit('adicionarIngrediente', $event)"
                    @remover-ingrediente="$emit('removerIngrediente', $event)" />
            </li>
        </ul>
    </article>
</template>


<style scoped>
/* Estilo para a classe 'categoria' */
.categoria {
    width: 19.5rem;
    /* Largura do artigo */
    padding: 1rem;
    /* Espaçamento interno */
    border-radius: 1rem;
    /* Bordas arredondadas */
    background: var(--branco, #FFF);
    /* Cor de fundo branca */
    box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
    /* Sombra */
    height: 100%;
    /* Altura total */

    display: flex;
    /* Layout flexível */
    flex-direction: column;
    /* Itens dispostos em coluna */
    align-items: center;
    /* Itens centralizados */
    gap: 2rem;
    /* Espaçamento entre itens */
}

/* Estilo para o cabeçalho da categoria */
.categoria__cabecalho {
    display: flex;
    /* Layout flexível */
    flex-direction: column;
    /* Itens dispostos em coluna */
    align-items: center;
    /* Itens centralizados */
    gap: 0.5rem;
    /* Espaçamento entre itens */
}

/* Estilo para a imagem da categoria */
.categoria__imagem {
    width: 3.5rem;
    /* Largura da imagem */
}

/* Estilo para o nome da categoria */
.categoria__nome {
    text-align: center;
    /* Texto centralizado */
    color: var(--verde-medio, #3D6D4A);
    /* Cor do texto verde médio */
    font-weight: 700;
    /* Negrito */
}

/* Estilo para a lista de ingredientes */
.categoria__ingredientes {
    display: flex;
    /* Layout flexível */
    justify-content: center;
    /* Itens centralizados horizontalmente */
    gap: 0.5rem;
    /* Espaçamento entre itens */
    flex-wrap: wrap;
    /* Itens quebram linha se necessário */
}
</style>