<script lang="ts">
import type IListaReceita from "@/interfaces/IListaReceita";
import CardReceitas from './CardReceitas.vue';
import type { PropType } from "vue/dist/vue.js";

export default {
    props: {
        listaReceita: {typo: Object as PropType<IListaReceita>, required: true}
    },

    components: { CardReceitas }
}
</script>


<template>
    <section class="selecionar-receitas">
        <h1 class="cabecalho titulo-receitas">Receitas</h1>

        <p class="paragrafo resultado-receitas">
            Resultados encontrados: 8
        </p>

        <p class="paragrafo dica">
            Veja as opções de receitas que encontramos com os ingredientes que você tem por aí!
        </p>

        <ul class="categorias">
            <CardReceitas v-for="receita in listaReceita" :key="receita"/>
        </ul>
    </section>
</template>


<style scoped>
/* Estilo para a classe 'selecionar-ingredientes' */
.selecionar-receitas {
    display: flex;
    /* Define como flexbox */
    flex-direction: column;
    /* Itens dispostos em coluna */
    align-items: center;
    /* Itens centralizados verticalmente */
}

/* Estilo para o título "ingredientes" */
.titulo-receitas {
    color: var(--verde-medio, #3D6D4A);
    /* Cor do texto verde médio */
    display: block;
    /* Exibe como bloco */
    margin-bottom: 1.5rem;
    /* Margem inferior */
}

.resultado-receitas {
    color: var(--verde-medio, #3D6D4A);
    /* Cor do texto verde médio */
    display: block;
    /* Exibe como bloco */
    margin-bottom: 1.5rem;
    /* Margem inferior */
    font-size: 1.3rem;
}

.dica {
    font-size: 1.5rem;
}
</style>