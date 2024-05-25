<script lang="ts">
import type { PropType } from 'vue';
import Tag from './Tag.vue';


export default {
    props: {
        ingredientes: {
            type: Array as PropType<string[]>, required: true
        }
    },

    components: { Tag }
}
</script>


<template>
    <section>
        <span class="subtitulo-lg sua-lista-texto">
            Sua lista:
        </span>
        <!-- Lista de ingredientes, mostrada apenas se houver ingredientes (v-if)-->
        <ul v-if="ingredientes.length" class="ingredientes-sua-lista">
            <!-- Itera sobre a lista de ingredientes e exibe um componente Tag para cada um -->
            <li v-for="ingrediente in ingredientes" :key="ingrediente">
                <Tag :texto="ingrediente" ativa /> <!-- Componente Tag exibindo o ingrediente -->
            </li>
        </ul>

        <!-- Mensagem exibida se a lista de ingredientes estiver vazia (v-else)-->
        <p v-else class="paragrafo lista-vazia">
            <img src="../assets/imagens/icones/lista-vazia.svg" alt="Ícone de pesquisa">
            Sua lista está vazia, selecione ingredientes para iniciar
        </p>
    </section>
</template>


<style scoped>
.sua-lista-texto {
    color: var(--coral, #F0633C);
    /* Cor do texto */
    display: block;
    /* Exibe como bloco */
    text-align: center;
    /* Alinha o texto ao centro */
    margin-bottom: 1.5rem;
    /* Margem inferior */
}

.ingredientes-sua-lista {
    display: flex;
    /* Define como flexbox */
    justify-content: center;
    /* Centraliza os itens */
    gap: 1rem 1.5rem;
    /* Espaçamento entre os itens */
    flex-wrap: wrap;
    /* Permite que os itens quebrem para a próxima linha */
}

.lista-vazia {
    display: flex;
    /* Define como flexbox */
    justify-content: center;
    /* Centraliza os itens */
    align-items: center;
    /* Alinha os itens ao centro */
    flex-wrap: wrap;
    /* Permite que os itens quebrem para a próxima linha */
    gap: 0.25rem;
    /* Espaçamento entre os itens */

    color: var(--coral, #F0633C);
    /* Cor do texto */
    text-align: center;
    /* Alinha o texto ao centro */
}
</style>