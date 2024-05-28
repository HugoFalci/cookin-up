<script lang="ts">
import type IListaReceita from "@/interfaces/IListaReceita";
import CardReceitas from './CardReceitas.vue';
import { obterReceitas } from "@/http/index";

export default {
    data() {
        return {
            receitas: [] as IListaReceita[]
        }
    },

    async created() {
        this.receitas = await obterReceitas(); // Carrega as categorias ao criar o componente
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
            <li v-for="receita in receitas" :key="receita.nome">
                {{ receita.nome }}
            </li>
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