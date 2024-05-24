<script lang="ts">
export default {
    props: {
        texto: { type: String, required: true },
        ativa: Boolean
    }
}
</script>

<template>
    <span class="tag" :class="{ ativa }">
        {{ texto }}
    </span>
</template>

<style scoped>
.tag {
    display: inline-block;
    /* Exibe como bloco em linha */
    border-radius: 0.5rem;
    /* Bordas arredondadas */
    min-width: 4.25rem;
    /* Largura mínima */
    padding: 0.5rem;
    /* Espaçamento interno (padding) */
    text-align: center;
    /* Alinha o texto ao centro */
    transition: 0.2s;
    /* Transição suave */
    color: var(--cinza);
    background: var(--cinza-claro);
    font-weight: 400;
}

.tag.ativa {
    color: var(--creme, #FFFAF3);
    /* Cor do texto */
    background: var(--coral, #F0633C);
    /* Cor de fundo */
    font-weight: 700;
    /* Peso da fonte */
}
</style>